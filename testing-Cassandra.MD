
# Building a Datastax Enterprise Application

## 1 - Building CRUD APPLICATION

### 1/10 - Introduction to KillrVideos

Videos and Comments
Data Model (Chetboko model)
CRUD Operations

### 2/10 - Sample CRUD Application

DAO
Mapper
Accessors
Bacths Operation

## Testing you application 
I - Testing Cassandra

### 1.1 - MOCK

### 1.1 - Unit tests

- Mock access to DB : EASYMOCK, MOCKITO, PowerMock

- Need to use embedded Cassandra : achilles junit, Cassandra-Unit
- Need to clean DB between each test
- Testing several version with Liquibase

- CQLTest        : https://cassandra.apache.org/doc/latest/development/testing.html
- Cassandra Unit : https://github.com/jsevellec/cassandra-unit
- Maven Cassandra Plugin : https://wiki.apache.org/cassandra/MavenPlugin
- Liquibase : https://github.com/liquibase
- CCM CCM (Cassandra Cluster Manager) https://github.com/riptano/ccm

### 1.2 - Integration Tests

- Cumcumber
- failsafe plugin and integration test
- Cassandra Distributed test https://github.com/apache/cassandra-dtest
- Docker Container `docker run -p 9042:9042 --name cass -d cassandra:3`

## Spark

## Graph

## Analytics
