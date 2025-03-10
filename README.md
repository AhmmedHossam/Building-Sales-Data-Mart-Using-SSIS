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

set identity_inser [table_name] on

....................................

set identity_inser [table_name] off

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

set identity_inser [table_name] on

...................................

set identity_inser [table_name] off

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

set identity_inser [table_name] on

......................................

set identity_inser [table_name] off

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










