# Jalali Utils (A Jalali extension for PostgreSQL)
Jalali Utils is a package for converting Gregorian dates to Jalali.
This package consists of the following functions:


```sql
format_jalali(TIMESTAMP WITH TIME ZONE, with_time BOOLEAN DEFAULT TRUE)
format_jalali(DATE)
jalali_part(TEXT, TIMESTAMP WITH TIME ZONE)
jalali_part(TEXT, DATE)
```

Examples:
```sql
SELECT format_jalali(now()); -->   1399/07/08 23:45:37
SELECT format_jalali(now(), false); -->   1399/07/08
SELECT format_jalali('2019-07-07', false); -->  1398/04/16
SELECT format_jalali('2021-03-20'); -->  1399/12/30 00:00:00
SELECT format_jalali('2021-03-20'::date); -->  1399/12/30
SELECT jalali_part('year', '2019-07-07 14:10:52.84937+04:30'); --> 1398
SELECT jalali_part('minute', '2019-07-07 14:10:52.84937+04:30'); --> 10
SELECT jalali_part('doy', '2019-07-07 14:10:52.84937+04:30'); --> 109
SELECT jalali_part('dow', '2019-07-07'); --> 4
```

`jalali_part` function can accept these values as the first parameter:
* year
* month
* day
* hour
* minute
* second
* doy (day of year)
* dow (day of week with index zero as saturday)
* quarter
* decade
* century

# Installation

## 1- Dependencies:

`sudo apt install postgresql-server-dev-15`

## 2- Run make to build and install

2.1 Download the zip file

`sudo unzip master.zip`

2.2 open the folter of content

`cd master`

2.3 Run make command inside the master directory:

`make`

2.4 Run make install too:

`sudo make install`

## 3- Login to postgres account and run psql:
```
root@server:#sudo su postgres
postgres@server:#
postgres@server:# psql
postgres=#
```

## 4- Select the database you want to install extension on it:

`postgres=# \c your_db_name`

`your_db_name=# `

## 5- Add the Extension to the database:

`your_db_name=#  CREATE EXTENSION jalali_utils;`

5.1 To remove the Extension from your database:

`your_db_name=#  DROP EXTENSION jalali_utils;`

# Running tests

> make installcheck
