<!-- loio3fbc107e282d48eab32678e33130bf9b -->

## SQL Reference for SAP Vora in SAP Data Hub

The SAP Vora SQL Reference describes all SQL data types, predicates, operators, expressions, functions, statements, error codes, and system views.
To use the search function for specific SQL statements, functions or operators, see the "customer documentation" guide on [SAP Help Portal](https://help.sap.com/viewer/DRAFT/98fe4b43ad664cba874e0fc7ea8ecc76/2.4.0/en-US "SQL Reference for SAP Vora in SAP Data Hub"). 

***

SAP Vora SQL is aligned with the SQL used by SAP HANA, so the SAP HANA SQL Reference is an additional valuable source of information. In general, SAP Vora SQL is a subset of SAP HANA SQL - the cases where Vora SQL differs from HANA SQL are pointed out explicitly. Also note that the public interface is aligned with the SQL 2011 standard. Test stetlasdjfdsf

<!-- loio36219daa81914ec286bf27d8ca4bdfe6 -->

## Notation

This reference uses BNF \(Backus-Naur Form\), a notation technique used to define programming languages. BNF describes the syntax of a grammar using a set of production rules and a set of symbols.

***

The following BNF items are used in this guide:

|Symbol|Meaning|
|------|-------|
|::=|Definition, left side is defined by right side|
|||OR operator|
|\( ... \)|Grouped tokens|
|\{ ... \}|Zero or more repetitions|
|\[ ... \]|Zero or one repetition|
|'...'|Literal final token|

<!-- loiod9617cf49f574e46b8d4e1960e1a904d -->

## Introduction to SQL

This section describes the SAP Vora database implementation of Structured Query Language \(SQL\).

***

<a name="loiod9617cf49f574e46b8d4e1960e1a904d__section_lb4_yby_wbb"/>

### Supported Languages and Code Pages

The SAP Vora database supports Unicode to allow the use of all languages in the Unicode Standard and 7 Bit ASCII code page without restriction.

***

<a name="loiod9617cf49f574e46b8d4e1960e1a904d__section_ipw_yby_wbb"/>

### Comments

You can add comments to improve the readability and maintainability of your SQL statements. Comments are delimited in SQL statements as follows:

-   Double hyphens "--". Everything after the double hyphen until the end of a line is ignored by the SQL parser.

-   "/\*" and "\*/". This style of commenting is used to place comments on multiple lines. All text between the opening "/\*" and closing "\*/" is ignored by the SQL parser.


***

<a name="loiod9617cf49f574e46b8d4e1960e1a904d__section_uby_yby_wbb"/>

### Identifiers

Identifiers are used to represent names used in SQL statement including table name, view name, synonym name, column name, index name, function name, procedure name, user name, role name, and so on. There are two kinds of identifiers, undelimited identifiers and delimited identifiers:

-   Undelimited table and column names must start with a letter and cannot contain any symbols other than digits or an underscore "\_".

-   Delimited identifiers are enclosed in the delimiter, double quotes. The identifier can then contain any character including special characters. "AB$%CD" is a valid identifier name for example.

-   Limitations:

-   Undelimited identifiers must not be equal to any reserved keywords. Using delimiters is a safe way to avoid conflicts with reserved keywords.

-   "\_SYS\_" is reserved exclusively for the database engine and is therefore not allowed at the beginning of schema object names.

-   The maximum length for identifiers is 127 characters.


***

<a name="loiod9617cf49f574e46b8d4e1960e1a904d__section_owz_yby_wbb"/>

### Identifiers and Case Sensitivity

Identifiers without double-quotes in SQL syntax are converted to upper case when processed by the server. For example, the statement `CREATE COLUMN TABLE MyTAB..` creates a table called MYTAB, whereas `CREATE COLUMN TABLE "MyTab"` creates a table called MyTab--and both tables can co-exist in the database.

Specifying identifiers without double-quotes is allowed but can cause ambiguity later when querying or performing operations on objects where casing in the identifier name is significant. A recommendation is to standardize to using double-quotes around all identifiers in SQL statements where ambiguity may be a concern.

***

<a name="loiod9617cf49f574e46b8d4e1960e1a904d__section_jtr_1dy_wbb"/>

### Quotation Marks

Single quotation marks \(`'`\) are used to delimit string literals. A single quotation mark itself can be represented using two single quotation marks \(`''`\). Double quotation marks are used to delimit identifiers. A double quotation mark itself can be represented using two double quotation marks.

<!-- loio766559d1440e4ac38ccb337ccefaaf22 -->

## Data Types

A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.

<!-- loiof5a79b91570f4d89b6eff4550b743808 -->

## Classification of Data Types

In the SAP Vora database, each data type can be classified by its characteristics as shown below.

***

|Classification|Data Type|
|--------------|---------|
|Boolean|BOOLEAN|
|Character|VARCHAR, CHAR|
|Other|NODE|
|Datetime|DATE, TIME, TIMESTAMP, INTERVAL|
|Numeric|TINYINT, SMALLINT, INTEGER, BIGINT, DECIMAL, REAL, DOUBLE|

<!-- loio94cfecb7c47742b79d02392981c53142 -->
