# DDL

## CREATE DATABASE

**Syntax**

```sql
CREATE SCHEMA [ IF NOT EXISTS ] database_name
```

**Parameters**

- database_name
  - Specifies the name of the database to be created.
- IF NOT EXISTS
  - Creates a database with the given name if it does not exist. If a database with the same name already exists, nothing will happen.

## CREATE TABLE

**Syntax**

```sql
CREATE TABLE [ IF NOT EXISTS ] tbl_name
```

**Parameters**

- tbl_name

  - The table name of the table to be created.
  - Table name can be specified as `db_name.tbl_name` to create the table in a specific database.

- IF NOT EXISTS
  - Prevent error occur if table with `tbl_name` already exist and skip create process.

### CREATE TABLE WITH COLUMNS

```sql
CREATE TABLE [ IF NOT EXISTS ] tbl_name
  (create_definition)
  [table_options]

create_definition: {
  col_name column_definition
}

column_definition: {
  data_type
  [PRIMARY KEY]
}

table_option: {
  STORAGE_EIGINE [=] engine_name
}

```

- create_definition

  - Specifies columns of a table.
  - Each column has a column name and type definition. See [Data Types]
  - Onle one column can be marked as Primary KEY

- table_option
  - Specify table storage engine. `hbase` is the only and default value for now.

### CREATE TABLE WITH SELECT

**Syntax**

```sql
CREATE TABLE [ IF NOT EXISTS ] tbl_name
  [table_options]
  AS query_expression

query_expression:
  SELECT ... ( a valid select statement)

```

**Parameters**

- query_expression
  - A SELECT statement that construct the table from base tables.

## CREATE VIEW

**Syntax**

```sql
CREATE VIEW [ IF NOT EXISTS ] view_identifier AS query
```

**Parameters**

- IF NOT EXISTS
  - Creates a view if it does not exist.
- view_identifier
  - Specifies a view name, which may be optionally qualified with a database name.
- query
  - A SELECT statement that constructs the view from base tables or other views.

## DESCRIBE TABLE

Obtaing table structure information.

**Syntax**

```sql
DESCRIBE TABLE [ IF EXISTS ] tbl_name
```

**Parameters**

- IF EXISTS

  - Prevent error occur if table not exist.

- tbl_name
  - Specify name of the table. Table name can be specified as `db_name.tbl_name` to describe the table in a specific database.

## DROP DATABASE

**Syntax**

```sql
DROP DATABASE [ IF EXISTS ] dbname
```

**Parameters**

- IF EXISTS
  - If specified, no exception is thrown when the database does not exist.
- dbname
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

## DROP VIEW

**Syntax**

```sql
DROP VIEW [ IF EXISTS ] view_identifier
```

**Parameters**

- IF EXISTS
  - If specified, no exception is thrown when the view does not exist.
- view_identifier
  - Specifies the view name to be dropped. The view name may be optionally qualified with a database name.

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
USE database_name
```

**Parameters**

- database_name
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

## SHOW VIEWS

List views in current database or a given database

**Syntax**

```sql
SHOW FULL TABLES [IN db_name] WHERE table_type = 'VIEW';
```

**Parameters**

- db_name
  - By specify `db_name` it will return views under the dabase.

## SHOW CREATE TABLE

Shows the [CREATE TABLE](#create-table) statement that creates the named table.

**Syntax**

```sql
SHOW CREATE TABLE tbl_name
```

**Parameters**

- tbl_name
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
  - An optional parameter that specifies a comma-separated list of columns belonging to the table_identifier table. Spark will reorder the columns of the input query to match the table schema according to the specified column list.
- VALUES ( { value | NULL } [ , … ] ) [ , ( … ) ]
  - Specifies the values to be inserted. Either an explicitly specified value or a NULL can be inserted. A comma must be used to separate each value in the clause. More than one set of values can be specified to insert multiple rows.
- query
  - A query that produces the rows to be inserted. It can be in one of following formats:
    - a SELECT statement
    - a TABLE statement
    - a FROM statement

## UPDATE

## DELETE

## LOAD(WIP)

# DQL

## COMMON EXPRESSION

## GROUP BY CLAUSE

## HAVING CLAUSE

## JOIN

## ORDER BY CLAUSE

## WHERE CLAUSE

# DCL

## GRANT(WIP)

## REVOKE(WIP)

[Data Types](#)
