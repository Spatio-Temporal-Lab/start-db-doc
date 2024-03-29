# DDL

## CREATE DATABASE

**Syntax**

```sql
CREATE DATABASE [ IF NOT EXISTS ] db_name
```

**Parameters**

- db_name
  - Specifies the name of the database to be created.
- IF NOT EXISTS
  - Creates a database with the given name if it does not exist. If a database with the same name already exists, nothing will happen.

## CREATE TABLE

There are three different manners for creating a new table

- Create a brand new table by defining column information.
- Reuse data from existing table with select query.
- Reuse metadata from an existing table with **LIKE**.

**Syntax**

```sql
create:
  createTableWithColumns
  createTableWithSelect
  createTableWithLike
```

### CREATE TABLE WITH COLUMNS

```sql
CREATE [ OR REPLACE ] TABLE [ IF NOT EXISTS ] table_identifier
  (create_definition)
  [WITH (with_options)]

create_definition: {
  col_name column_definition
}

column_definition: {
  data_type
  [PRIMARY KEY]
}

with_options:
    with_option [[,] with_option] ...

with_option: {
  STORAGE [=] storage_name
}

```

- table_identifier

  - Specify qulified name of the table.
  - Table name can be specified as `user_name.db_name.tbl_name` to describe the table in a specific database of a certain user.

- create_definition

  - Specifies columns of a table.
  - Each column has a column name and type definition. See [Data Types]
  - Onle one column can be marked as PRIMARY KEY

- with_options
  - Specify table metadata.
  - STORAGE specifiy how data stored. `hbase` is the only and default value for now.

### CREATE TABLE WITH SELECT

**Syntax**

```sql
CREATE [ OR REPLACE ]  TABLE [ IF NOT EXISTS ] table_identifier
  AS query_expression
  [WITH (with_options)]

query_expression:
  SELECT ... ( a valid select statement)

with_options:
    with_option [[,] with_option] ...

```

**Parameters**

- query_expression
  - A SELECT statement that construct the table from base tables.

### CREATE TABLE WITH LIKE

Use _CREATE TABLE ... LIKE_ to create an empty table based on the definition of another table, including column information.

**Syntax**

```sql
CREATE [ OR REPLACE ] TABLE [ IF NOT EXISTS ]
  DESTINATION=table_identifier
  LIKE ORIGINATION=table_identifier
```

**Parameters**

- DESTINATION
  - Specify the target qualified table name.
- ORIGINATION
  - Specify the original qualified table name.

## DESCRIBE TABLE

Obtaing table structure information.

**Syntax**

```sql
DESCRIBE TABLE [ IF EXISTS ] table_identifier
```

**Parameters**

- IF EXISTS

  - Prevent error occur if table not exist.

- table_identifier
  - Specify name of the table. Table name can be specified as `db_name.tbl_name` to describe the table in a specific database.

## DROP DATABASE

**Syntax**

```sql
DROP DATABASE [ IF EXISTS ] db_name
```

**Parameters**

- IF EXISTS
  - If specified, no exception is thrown when the database does not exist.
- db_name
  - Specifies a database name

## DROP TABLE

**Syntax**

```sql
DROP TABLE [ IF EXISTS ] table_identifier
```

**Parameters**

- IF EXISTS
  - If specified, no exception is thrown when the table does not exist.
- table_identifier
  - Specifies the table name to be dropped. The table name may be optionally qualified with a database name.

## TRUNCATE TABLE

**Syntax**

```sql
TRUNCATE TABLE table_identifier
```

**Parameters**

- table_identifier
  - Specifies a table name, which may be optionally qualified with a database name.

## USE DATABASE

**Syntax**

```sql
USE db_name
```

**Parameters**

- db_name
  - Name of the database will be used. If the database does not exist, an exception will be thrown.

## SHOW DATABASES

Lists the databases on the start-db server.

**Syntax**

```sql
SHOW DATABASES;
```

## SHOW TABLES

Lists tables in current dabase or a given database.

**Syntax**

```sql
SHOW TABLES [IN db_name]
```

**Parameters**

- db_name
  - It will show all tables under current databse. By specify `db_name` it will show all tables under the dabase.

## SHOW CREATE TABLE

Shows the [CREATE TABLE](#create-table) statement that creates the named table.

**Syntax**

```sql
SHOW CREATE TABLE table_identifier
```

**Parameters**

- table_identifier
  - Specify name of the table. Table name can be specified as `db_name.tbl_name`.

# DML

## INSERT INTO

**Syntax**

```
INSERT INTO [ TABLE ] table_identifier [ ( column_list ) ]
    { VALUES ( { value | NULL } [ , ... ] ) [ , ( ... ) ] | query }
```

**Parameters**

- table_identifier
  - Specifies a table name, which may be optionally qualified with a database name.
- column_list
  - An optional parameter that specifies a comma-separated list of columns belonging to the table_identifier table.
- VALUES ( { value | NULL } [ , … ] ) [ , ( … ) ]
  - Specifies the values to be inserted. Either an explicitly specified value or a NULL can be inserted. A comma must be used to separate each value in the clause.
  - More than one set of values can be specified to insert multiple rows.
- query
  - A query that produces the rows to be inserted. It can be in one of following formats:
    - a SELECT statement
    - a TABLE statement
    - a FROM statement

## UPDATE

Modifies rows in a table.

**Syntax**

```
UPATE table_identifier
  SET assignment_list
  WHERE boolean_expression

table_identifier: {
  tbl_name
}

assignment_list:
  assignment [, assignment] ...

assignment:
  col_name = value
```

**Parameters**

- table_identifier

  - Specify name of the table. Table can be specified as `db_name.tbl_name`.

- assignment_list

  - Assignment list set values for each column to be modifed.
  - Column can be accessed in an assignment expression. For example `UPDATE t1 SET col1 = col1+1`.
  - Assignments are evaluated from left to right.

- boolean_expression
  - boolean_expression is an expression that evaluates to ture for each row to be updated. For detail syntax, see [WHERE CLAUSE](#where-clause)

## DELETE

Remove rows from a table.

**Syntax**

```
DELETE from table_identifier
  WHERE boolean_expression
```

**Parameters**

- table_identifier

  - Specify name of the table. Table can be specified as `db_name.tbl_name`.

- boolean_expression
  - boolean_expression is an expression that evaluates to ture for each row to be updated. For detail syntax, see [EXPRESSIONS](#expressions)

## LOAD (WIP)

Read rows from a text files into a table at a very high speed.

**Syntax**

```
LOAD DATA
  INFILE 'file_name'
  [REPLACE | IGNORE]
  INTO TABLE table_identifier
  [FIELDS
    [TERMINATED BY 'string']
    [[ESCAPED BY 'char']]
  ]
  [LINES
    [STARTING BY 'string']
    [TERMINATED BY 'string']
  ]
  [IGNORE number {LINES}]
```

**Parameters**

- 'file_name'
  - Specify local file path which contains data to be loaded into table
- REPLACE | IGNORE
  - For handle duplicate key error. With `REPLACE`, new rows wil replace rows with same key value, while IGNORE will discard them.
- FIELDS and LINES
  - Used for handle fields and lines in file
  - Field terminated by '\t', escapsed by '\\' by default
  - Line start by '' and terminated by '\n' by default
- IGNORE number LINES
  - Used to ignore lines at the start of th file, for example you can use 'IGNORE 1' to skip header containing column names. Default value is `0`.

# DQL

## SELECT Statement

Select statement is used for retrieve rows selected from one or more tables.

In START-DB, you can also use SELECT statement without FROM to generate a result set projecting the columns and values that you've specified.

**Syntax**

```
SELECT
  project_item [, project_item] ...
  [FROM table_reference]
  [WHERE boolean_expression]
  [GROUP BY col_name [ASC|DESC]]
  [LIMIT {[offset,] row_count}]

project_item {
  expression [[AS] columnAlias] |
  tableAlias
}
```

**Parameters**

- project_item

  - Each project_item indicates a column that you want to retrieve.
  - A project_item can come from a column or produced from an expression.
  - There must be at least one project_item.

- table_reference

  - It can be a table_identifer or a joined table. See [JOIN CLAUSE](#join-clause)

- WHERE boolean_expression

  - If given, indicate the condition or conditions that rows must satisfy to be selected. See [WHERE CLAUSE](#where-clause)

- GROUP BY

  - Used for grouping selected results. See [GROUP BY CLAUSE](#group-by-clause)

- ORDER BY

  - Specify rows order in result

- LIMIT
  - Used to constrain the number of rows returned.
  - With one argument, the value specifies the number of rows to return from the begining. With two argument, the first tells the offset and the second specify the max number of rows to return.

## EXPRESSIONS

This section lists the grammar rules that expressions must follow in START-DB.

## GROUP BY CLAUSE

Used for grouping results returned for select statement.

**Syntax**

```
GROUP BY {col_name | expr | position} [ASC|DESC]
```

## JOIN CLAUSE

START-DB supports JOIN syntax for the `table_reference` of _SELECT_ statements.

**Syntax**

```sql
table_reference:
  table_identifier [, table_identifier]*
  | table_reference [ NATURAL ] [ { LEFT | RIGHT | FULL } [ OUTER ] ] JOIN table_reference [ joinCondition ]
  | table_reference CROSS JOIN table_reference


joinCondition:
  ON boolean_expression
```

## ORDER BY CLAUSE

ORDER BY specify order for select results.

**Syntax**

```sql
ORDER BY {col_name | expr }
      [ASC | DESC], ...
```

## WHERE CLAUSE

Indicates the condition or conditions that rows must satisfy to be selected. `boolean_expression` is an [EXPRESSION](#expressions) that evaluate to true for each row to be selected. The select statement selects all rows if there is not WHERE clause.

**Syntax**

```sql
WHERE boolean_expression
```

In the where expression, you can use [functions and operators] that START-DB supports.

[data types]: #todo-link-to-data-types
[functions and operators]: #todo-link-to-functions
