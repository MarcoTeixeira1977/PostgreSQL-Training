Creating a PostGIS database
===========================

Creating a PostGIS database involves the same steps as a normal POstgreSQL database.  Enabling PostGIS extensions on the database gives a greater variety of data types and fucntions.


Create a normal database
------------------------

For this purpose we're going to use our training database so we can skip this step.

- [CREATE DATABASE documentation](https://www.postgresql.org/docs/current/static/sql-createdatabase.html)

```PLpgSQL
CREATE DATABASE training;
```

Add PostGIS extensions
----------------------

Making a spatial database involves initially adding PostGIS extensions.

On the new database, run the command to add PostGIS extensions.

- [CREATE EXTENSION documentation](https://www.postgresql.org/docs/current/static/sql-createextension.html)

```PLpgSQL
CREATE EXTENSION postgis;
```

Create a normal table
---------------------

Run a create table statement.

- [CREATE TABLE documentation](https://www.postgresql.org/docs/current/static/sql-createdatabase.html)

```PLpgSQL
CREATE TABLE postcodes_geo (
    postcode varchar(8),
    positional_quality_indicator integer,
    po_box_indicator char(1),
    total_number_of_delivery_points integer,
    delivery_points_cplc integer,
    domestic_delivery_points integer,
    non_domestic_delivery_points integer,
    po_box_delivery_points integer,
    matched_address_premises integer,
    unmatched_delivery_points integer,
    country_code varchar(9),
    nhs_regional_ha_code varchar(9),
    nhs_ha_code varchar(9),
    admin_county_code varchar(9),
    admin_district_code varchar(9),
    admin_ward_code varchar(9),
    postcode_type char(1),
    CONSTRAINT pk_postcodesgeo_postcode PRIMARY KEY(postcode)
);
```

Add a geometry column
---------------------

- [AddGeometryColumn documentation](https://postgis.net/docs/AddGeometryColumn.html)

```PLpgSQL
SELECT AddGeometryColumn ('postcodes_geo','geom',0,'POINT',2);
```

Loading CSV data
----------------

Loading CSV data can be done in the same way as we did previously.  We know that the final column includes valid well known text POINT data.

- [COPY documentation](https://www.postgresql.org/docs/current/static/sql-copy.html)

```PLpgSQL
COPY postcodes_geo FROM 'C:\Development\DaveBathnes\PostgreSQL-Training\data\codepoint.csv' HEADER CSV;
```

Set the SRID of the column
--------------------------

To save the Spatial Reference System being used in the column we can use a PostGIS function to set this value.

The data is British National Grid so we can set the SRID to 27700.

- [UpdateGeometrySRID documentation](https://postgis.net/docs/UpdateGeometrySRID.html)

```PLpgSQL
SELECT UpdateGeometrySRID('postcodes_geo','geom',27700);
```