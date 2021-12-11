# Financial-Analysis-Using-COVID-Data
CMPT 726 Big Data Project

## Step 1
Create the schema for all the tables in cassandra.<br/>
We will be using the following tables for our project.

Create keyspace for the project<br/>
**CREATE KEYSPACE dataflix WITH REPLICATION = {'class': 'SimpleStrategy', 'replication_factor': 1 };**

Create the following tables
Covid19 data related tables:

**CREATE TABLE dataflix.covid19_cases_us (<br/>
    date date,<br/>
    city text,<br/>
    province text,<br/>
    new_cases_us int,<br/>
    total_cases_us int,<br/>
    PRIMARY KEY (date, city, province)<br/>
)<br/>**

**CREATE TABLE dataflix.covid19_deaths_us (
    date date,
    city text,
    province text,
    new_deaths_us int,
    total_deaths_us int,
    PRIMARY KEY (date, city, province)
)**

**CREATE TABLE dataflix.covid19_cases_global (
    date date,
    country text,
    new_cases_global int,
    total_cases_global int,
    PRIMARY KEY (date, country)
)**

**CREATE TABLE dataflix.covid19_deaths_global (
    date date,
    country text,
    new_deaths_global int,
    total_deaths_global int,
    PRIMARY KEY (date, country)
)**

**CREATE TABLE dataflix.covid19_recovered_cases_global (
    date date,
    country text,
    new_recovered_global int,
    total_recovered_global int,
    PRIMARY KEY (date, country)
)**

Stock market Related table

**CREATE TABLE dataflix.stocks (
    stock_type text,
    date date,
    close float,
    high float,
    low float,
    open float,
    volume float,
    PRIMARY KEY (stock_type, date)
)**

Cryptocurrencies market related tables:

**CREATE TABLE dataflix.commodities (
    type text,
    market text,
    date date,
    close float,
    high float,
    low float,
    open float,
    volume float,
    PRIMARY KEY (type, market, date)
)**

Foreign Exchange Market realted table:

**CREATE TABLE dataflix.forex (
    forex_type text,
    date date,
    close float,
    high float,
    low float,
    open float,
    volume float,
    PRIMARY KEY (forex_type, date)
)**

Commodities market realted table:

**CREATE TABLE dataflix.commodities (
    type text,
    market text,
    date date,
    close float,
    high float,
    low float,
    open float,
    volume float,
    PRIMARY KEY (type, market, date)
)**























