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

# Commands

(1) - Creating Graph
 => Associated to a KeySpace
 => In reality multiple keyspaces underlying

- Listing amd Describing Graph

- Dropping Graph

```cql
schema.config().option('graph.schema_mode').set('Development')
schema.config().option('graph.allow_scan').set('true')
```

[Create a graph](https://docs.datastax.com/en/datastax_enterprise/5.0/datastax_enterprise/graph/reference/system/refOption.html)

```cql
system.graph("KillrVideo").create()

system.graph("KillrVideo").ifNotExists().create()

# Define some options
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

# Change property later
schema.config().option('graph.schema_mode').set('Development')
schema.config().option('graph.allow_scan').set('true')    
```

Count Number of nodes
```cql
g.V().count()
```
Create a vertex
juliaChild = graph.addVertex(label,'author', 'name','Julia Child', 'gender','F')



 
