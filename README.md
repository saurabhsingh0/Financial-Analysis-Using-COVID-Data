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
);<br/>**

**CREATE TABLE dataflix.covid19_deaths_us (<br/>
    date date,<br/>
    city text,<br/>
    province text,<br/>
    new_deaths_us int,<br/>
    total_deaths_us int,<br/>
    PRIMARY KEY (date, city, province)<br/>
);<br/>**

**CREATE TABLE dataflix.covid19_cases_global (<br/>
    date date,<br/>
    country text,<br/>
    new_cases_global int,<br/>
    total_cases_global int,<br/>
    PRIMARY KEY (date, country)<br/>
);<br/>**

**CREATE TABLE dataflix.covid19_deaths_global (<br/>
    date date,<br/>
    country text,<br/>
    new_deaths_global int,<br/>
    total_deaths_global int,<br/>
    PRIMARY KEY (date, country)<br/>
);<br/>**

**CREATE TABLE dataflix.covid19_recovered_cases_global (<br/>
    date date,<br/>
    country text,<br/>
    new_recovered_global int,<br/>
    total_recovered_global int,<br/>
    PRIMARY KEY (date, country)<br/>
);<br/>**

Stock market Related table:

**CREATE TABLE dataflix.stocks (<br/>
    stock_type text,<br/>
    date date,<br/>
    close float,<br/>
    high float,<br/>
    low float,<br/>
    open float,<br/>
    volume float,<br/>
    PRIMARY KEY (stock_type, date)<br/>
);<br/>**

Cryptocurrencies market related table:

**CREATE TABLE dataflix.crypto (<br/>
    cryptotype text,<br/>
    date date,<br/>
    close float,<br/>
    high float,<br/>
    low float,<br/>
    open float,<br/>
    volume float,<br/>
    PRIMARY KEY (cryptotype, date)<br/>
);<br/>**

Foreign Exchange Market realted table:

**CREATE TABLE dataflix.forex (<br/>
    forex_type text,<br/>
    date date,<br/>
    close float,<br/>
    high float,<br/>
    low float,<br/>
    open float,<br/>
    volume float,<br/>
    PRIMARY KEY (forex_type, date)<br/>
)**<br/>

Commodities market realted table:

**CREATE TABLE dataflix.commodities (<br/>
    type text,<br/>
    market text,<br/>
    date date,<br/>
    close float,<br/>
    high float,<br/>
    low float,<br/>
    open float,<br/>
    volume float,<br/>
    PRIMARY KEY (type, market, date)<br/>
)**<br/>

## Step 2
We can execute the dataflix.sh file to run the entire project. Command to execute dataflix.sh file:<br/>
**sh dataflix.sh** <br/>

It does the following things: <br/>
1. It runs all the spark jobs and saves the data in the cassandra db. All the files like crypto.py, stocks.py, commodities.py and forex.py will perform etl and save all the respective data in cassandra tables created as there is a for loop inside the script which will run all the spark jobs and save the data for the respective datasets into the cassandra Db with dataflix as keyspace and crypto, stocks, commodities and forex tables. <br/>
2. The second part of the script will train the model by fetching the data from the cassandra db, after which we perform further etl and aggregate functions as per the requirements of the ml models. After the etl and aggregate operations are performed, the cleaned data is saved and used for visualization using Tableau. After training and validating the model, the model is saved in `model_train` folder for predictions.
3. The report and power point presentation for visualization results can be found below:
report pdf:
ppt:


## The project uses following directories

the soruce directory has following files and folders:<br/>

**dataflix.sh**

**datasets**<br/>
	-covid<br/>
	-stocks<br/>
	-forex<br/>
	-commodities<br/>
	-crypto<br/>

**insert_to_cassandra**<br/>
	-covid.py<br/>
	-crypto.py<br/>
	-stocks.py<br/>
	-commodities.py<br/>
	-forex.py<br/>
	
**load_data**<br/>
	-load_covid.py<br/>
	-load_crypto.py<br/>
	-load_stocks.py<br/>
	-load_commodities.py<br/>
	-load_forex.py<br/>

**model_train**<br/>
	-models/model_type/individual_models<br/>
	-cypto_model.py<br/>
	-stocks_model.py<br/>
	-commodities_model.py<br/>
	-forex_model.py <br/>


























