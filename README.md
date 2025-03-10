# Building-Sales-Data-Mart-Using-SSIS

# 1- STEP1 : Building data warehouse (star schema)

DIM1 : dim_product


unq keys:

surrogate key : product_key 

business key : product_id

meta data keys :

source_system_code -- to know sys

start_date default(getdate())

end_date

is_current varvhar(1)

inserting unkown record incase of unkown product_id (business key)

set identity_insert [table_name] on

....................................

set identity_insert [table_name] off

create index on business key

-----------------------------------

DIM2 : dim_customer


unq keys:

surrogate key : customer_key.

business key : customer_id

meta data keys :

source_system_code -- to know sys

start_date default(getdate())

end_date

is_current varvhar(1)

inserting unkown record incase of unkown product_id (business key)

set identity_insert [table_name] on

...................................

set identity_insert [table_name] off

create index on business key

-----------------------------------

DIM3 : dim_terriotry


unq keys:

surrogate key : terriotry_key.

business key : terriotry_id

meta data keys :

source_system_code -- to know sys

start_date default(getdate())

end_date

is_current varvhar(1)

inserting unkown record incase of unkown product_id (business key)

set identity_insert [table_name] on

......................................

set identity_insert [table_name] off

create index on business key

-----------------------------------

DIM : dim_date


unq keys:

surrogate key : order_date_key.

-----------------------------------

Fact table sales : 

define PK

creat fk constrains with surrogate keys from dims

creat indexes on fks 

![Screenshot 2025-03-10 144322](https://github.com/user-attachments/assets/e0248011-b1c2-494a-b9ea-e53b59fecd64)


# 2-step2: SSIS


Dim 1 : dim_customer ETL

step 1 : identify source and destination databases

step 2 : adding data flow task 

step 3 : Adding source using OLE DB SOURCE

step 3.1 : choosing data base soucre

step 3.2 : picking recq table or by using sql command

step 4 : add more data from another table using LOOKUP transformation ( full cache, direct row to no match o/p)

Key Features of the Lookup Transformation:
Match Columns: The transformation compares columns in the input data to those in the reference data to find a match. You specify which columns to use for matching.

Output: After finding a match, the transformation can output additional columns from the reference data, allowing you to enhance or update the incoming data with related values (e.g., adding a CountryName based on CountryCode).

Handling Non-Matches: There are two main ways to handle rows that don't match the reference data:

Fail the Row: If no match is found, the row is discarded.
Default Value: If no match is found, you can output a default value (e.g., NULL or a specified default).
Caching Options:

Full Cache: The lookup data is fully cached into memory. This is the fastest option when the reference data is not very large.
Partial Cache: Only the matching rows are cached, and non-matching rows are queried on-demand.
No Cache: Every row is queried directly from the reference data source, which can slow down performance but ensures that you always get the most up-to-date data.

step 4.1 : define source data base

step 4.2 : define table by choosing table, view or by query

step 4.3 : adding to quer

union all

select null, null, null 

note1 : 3 nulls cause i have 3 columns in main select query

note2 : too add values with null models with matching values

step 4.4 : check onm req o/p column to be added

step 5 : add another look up 

step 5.1 : connect between two lookups by matching o/p's

step 5.3 : add source data base wrtie eq qurey

step 6 : replacing null values with UNKOWN using drived 

step 6.1 : choosing req column 

step 6.2 : choosing insull funcs and spicify req o/p exp

![01_product_table](https://github.com/user-attachments/assets/dfc44761-cf6d-42f9-a33d-049b159aceb8)





















