# Keynote: [ETL Is Dead; Long-Live Streams](https://qconsf.com/sf2016/keynote/rise-real-time)

Wednesday, Nov. 9 2016

@nehanarkhede - Neha Narkhede (Confluent)

## Intro

Old World: Data in one of two places, Operational Database and Data Warehouse

Single-server databases are replaced by a myriad of distributed systems

Many more types of data sources beyond transactional data - logs, sensors, metrics, etc.

Stream data is increasing ubiquitous, need for faster data processing than daily

Technology hasn't caught up yet, end up with web of apps, messaging queues, databases - a mess!

Stream changelogs from databases into other systems, transform the data

## A Short History of Data Integration

Surfaced in the 1990's, retail organizations analyzing buyer trends

Extract data from databases, Transform into destination warehouse schema, Load into system (ETL)

Drawbacks of ETL:
* Need for a global schema
* Data cleansing and curation is manual, error-prone
* Operational cost is high - slow, takes times, resource intensive
* Narrowly focus on connecting data and warehouses, do it in batch

Early take on real-time ETL = Enterprise Application Integration (EAI)

Service buses and MQs under hte cover, weren't scalable

EAI = real-time, not scalable, ETL - scalable, batch

Streaming platform would be real-time and scalable!

## Streaming Platform

Requirements
* High volume, high diversity data
* Real-time from the ground-up, event-centric
* Forward-compatible data architecture, ability to add more apps that process data differently
* Fault-tolerance, parallelism, security

Web app/mobile app/APIs => __Streaming Platform__ => Hadoop/Security/Monitoring
* Decouple data sources and consumers, don't need to know about each other

Example:
* Logs extracted as unstructured text
* Data is ~~transformed~~ cleansed
* Load data into warehouse
* Transform again with additional data in warehouse
* Must repeat business logic for each new source

Streaming platform serves as a central nervous system for your company's data

## Apache Kafka

Adopted at 1000's of companies, can handle billions of transactions a day.

Kafka is the de-facto storage of choice for stream data

Multiple log readers (sequential), one writer (append-only)

Build readers into a pub-sub model, multiple subscribers

Offers a scalable messaging platform
