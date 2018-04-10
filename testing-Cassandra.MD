
# Building a Datastax Enterprise Application

### 1/10 - Designing your datamodel

* Introduction to KillrVideo Application
* ds220
* Videos and Comments
* Data Model (Chetboko model)
* CRUD Operations
* CQL files

### 2/10 - Create your DAOs (CRUD)

* Understanding drivers (dse)
* PrepareStatement
* Batchs Operation
* Mapper & Accessors
* Spring Data

### 3/10 - Unit Testing

* Mocking woith PowerMock/Mockito
* Embedded Cassandra : Cassandra-Unit
* Embedded Cassandra : Achilles unit
* Embedded Cassandra : Maven Cassandra Plugin : https://wiki.apache.org/cassandra/MavenPlugin
* Embedded Cassandra : Simulacron https://github.com/riptano/simulacron

### 4/10 - Integration Testing

* Liquibase https://github.com/liquibase
* Scassandra https://github.com/scassandra/scassandra-server
* CQLTest https://cassandra.apache.org/doc/latest/development/testing.html
* CCM CCM (Cassandra Cluster Manager) https://github.com/riptano/ccm
* Cassandra Distributed test https://github.com/apache/cassandra-dtest
* Cumcumber
* failsafe plugin and integration test
* Docker Container `docker run -p 9042:9042 --name cass -d cassandra:3`

http://niels.nu/blog/2017/spring-cassandra-integration-tests.html

### 5/10 - Designing you API

* REST API
* GRPC API
* GraphQL API

### 6/10 - Build UI and end-user applications

* kmow your queries
* fail fast do not iterate on not working file
* NodeJS here

### 7/10 - Performance Testing

* cassandra-stress
* ccm
* aws
* gatling plugin

### 8/10 - Search

* cassandra-stress
* ccm
* aws
* gatling plugin

### 9/10 - Graph

* cassandra-stress
* ccm
* aws
* gatling plugin

### 10/10 - Analytics

* Cassandra and time series
* Spark

