Introduction to PostgreSQL
==========================

PostgreSQL (or Postgres for short) is a popular open source object relational database server.

- Runs on all major operating systems, including Linux, UNIX (AIX, BSD, HP-UX, SGI IRIX, macOS, Solaris, Tru64), and Windows.
- It is fully ACID compliant (standard database speak - Atomicity, Consistency, Isolation, Durability).
- PostgreSQL runs stored procedures in more than a dozen programming languages, including Java, Perl, Python, Ruby, Tcl, C/C++, and its own PL/pgSQL, which is similar to Oracle's PL/SQL

| Term | Description |
| ---- | ----------- |
| Relational | A relational database is a set of tables containing data fitted into predefined categories. Each table (which is sometimes called a relation) contains one or more data categories in columns. Each row contains a unique instance of data for the categories defined by the columns.  |
| Object-Relational | An object relational database uses an object-oriented model.  Objects, classes and inheritance are supported. Particularly in PosgreSQL, this includes table inheritance. |
| SQL | Structured Query Language.  Different database servers use diferent 'flavours' of SQL.  PostgreSQL SQL implementation strongly conforms to the ANSI-SQL:2008 standard. |
| Open Source | The PostgreSQL Licence gives you the freedom to use, modify and distribute PostgreSQL in any form you like, open or closed source. Any modifications, enhancements, or changes you make are yours to do with as you please. |
| Extensible | PostgreSQL includes a framework that allows developers to define and create their own custom data types along with supporting functions and operators that define their behavior. As a result, a host of advanced data types have been created that range from geometric and spatial primitives to network addresses to even ISBN/ISSN (International Standard Book Number/International Standard Serial Number) data types, all of which can be optionally added to the system.  |

Limits
------

There are some data limits within PostgreSQL but they are quite high.

| Limit | Value |
| ----- | ----- |
| Maximum Database Size | Unlimited |
| Maximum Table Size | 32 TB |
| Maximum Row Size | 1.6 TB |
| Maximum Field Size | 1 GB |
| Maximum Rows per Table | Unlimited |
| Maximum Columns per Table | 250 - 1600 depending on column types |
| Maximum Indexes per Table | Unlimited |
