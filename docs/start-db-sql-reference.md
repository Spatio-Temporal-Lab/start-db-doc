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

### CREATE TABLE WITH COLUMNS

### CREATE TABLE WITH SELECT(WIP)

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

## SHOW TABLES

## SHOW VIEWS

## SHOW CREATE TABLE

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
