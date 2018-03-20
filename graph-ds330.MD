#  DS330: DataStax Enterprise Graph

## Introduction

#### Architecture
- TinkedPop => Traversal Language & Data (server)
- Cassandra => Storage
- Solr 		=> full text search
- Spark 	=> Analytic Transversal
- Comprehensive security
- Visualization with the studio
- Integrated to ops center

#### Property Graph
- Definitions
 => Vertices or Nodes
 => Edges are relationships
 => Properties on both entity model, relations attributes

#### Gremlin
 => turing complete and functional in nature
 => income edge
 => g.V().has("person", "name", "Johny Depp")
 		 .in("actor").has("year", gte(2010)).
 		 values("title", "year")
 => OLTP = OLAP Engine

## Use Cases
 - Internet of things
 - Customer360
 - Personalization
 - Recommendation Engine
 - Fraud Detection
 - Path Finding
 - Social
 - Ranking/Credibility

### Traversal
  - Breatdh-first (parcours en largeur)
  - Depth-fisrt.  (parcours en longueur)
  - Filtering
  - Aggregating
  - BackTracking

## Architecture Tools]

- Technology
 => TinkerPop (schema provided by)
 => To secret
 => All other components

#### Tooling
 => Datastax Studio (WEB)
 => Gremlin Console (CLI)
 => Fuzzy yopic for OLAP vs OLTP
 => Spark will be for OLAP & Spark
 => LOAD TABLE => CSV
 => LOAD GRAPH ? 
  - Dialect Json/Graph
  - Graph Loader loading .groovy
 => DSE OPSCenter
 => DSE Analytics Web UI

[Property Graph]

- Definitioin
 => Directed, binary, attributes
 => Multigraph - multiple edges to single nodes

- Node
 => UNIQUE ID     : unique ids
 => LABEL         : it the type
 => PROPERTIES    : other properties
 => MULTIPROPERTY : appears several times, appear as an array
    * ONLY TO VERTICE, NOT TO EDGES
 => METADATAPROPERTIES: properties of properties
 => ACL on Properties

- Key Terms
 => SUBGRAPH. : subset of a graph
 => INCIDENT Edge : l'un des noeuds colle le noeud
 => incoming & outgoing edges (directed)
 => AJACENT : Vertices are If connected to by an edge
 => PATH : sequence of edge and vertex (can start with edge and/or vertex)
 => SIMPLE : cannot visit the same node twice
 => CYCLIC : multiple accesses to a single node
 => DEGREE OF VERTEX : number of edges associated to the vertex
 => IN DEGREE : number of edge which comes

## Commands

#### Managing Graph

```cql

# --- Creations...
system.graph("KillrVideo").create()
system.graph("KillrVideo").ifNotExists().create()
system.graph("KillrVideo")
       .option("graph.replication_config")
        .set("{'class' : 'NetworkTopologyStrategy', 'dc1' : 3 }").
       .option("graph.system_replication_config")
        .set("{'class' : 'NetworkTopologyStrategy', 'dc1' : 3 }")
       .option("graph.schema_mode").set("Development")
       .option("graph.allow_scan").set("false")
       .option("graph.default_property_key_cardinality").set("multiple")
       .option("graph.tx_groups.*.write_consistency").set("ALL").
      .ifNotExists().create()

# --- Edit properties (later)
schema.config().option('graph.schema_mode').set('Development')
schema.config().option('graph.allow_scan').set('true')


```

Under the hood multiple keyspaces are created : 
- GraphName : Graph Data, verticesm edges, properties
- GraphName_system : system datam schema, variables
- GraphName_pvt: Partitioned vertices (huge number of edges) large vertices

- Listing and describing Graphs

```cql
system.graphs()
system.describe()
system.graph("KillrVideo").describe()
```

- Dropping Graphs

```cql
system.graph("KillrVideo").drop()
```

#### Working with SCHEMA

- Property Keys: unique key (name), data type, cardinatlitym ,meta-properties
Vertex Labels
Edge Labels
Indexes

```cql
schema.getClass();

# Create Property Keys
# Types : Numbers, booleamn Text, UUid, Timestamp, Duration, Point, Linestring, Polygon
schema.propertyKey("year").Int().single.create();
schema.propertyKey("sample").Text().multiple().create();
schema.propertyKey("production").Text().multiple().
   properties("source", "date").create();
   
# Create Vextex Labels (need unique LABEL)
schema.vertexLabel("movie").properties("year", "sample", "poduct").create();
# If possible reuse the property
schema.vertexLabel("person").properties("year").create();

# Edge Labels (label, cardinalitym propertyKeys, domain, range)
# No multiple Properties
schema.edgeLabel("rated")
      .single()
      .properties("year", "sample", "poduct")
      .connection("user", "movie") // from domain user to range movie
      .create();
schema.edgeLabel("knows")
      .single()
      .connection("user", "movie") // from domain user to range movie
      .connection("user", "person") // from domain user to range movie
      .connection("person", "user") // from domain user to range movie
      .create();
      
# Create Index : vertex, property or edge
schema.edgeLabel("knows").describe()

# Remove all 
schema.clear()

```
#### Custom vertex ids

Use default partition id
Default is fetching communities/subgraph
community_id +  member_id + label (vertex Type)
```cql
g.V().hasId("{~label=movie, member_id=0, communitu_id=4567}")
```
Cstuom Vertex ID
partitionKey
clusteringKey
~label
```cql
schema.vertexLabel("user")
      .partitionKey("userName")
      .properties("p1","p2")
      .create();
      
schema.vertexLabel("movie")
      .partitionKey("year", "sdsd")
      .clusteringKey("movieId)
      .properties("p1","p2")
      .create();
      
g.V().hasId("{~label=movie,userName=toto}")
```

- Count Number of nodes

```cql
g.V().count()
```

- Create a vertex

```cql
juliaChild = graph.addVertex(label,'author', 'name','Julia Child', 'gender','F')
```

- Op

```cql
commad
```

 Multi-properties are associated with vertices
  
