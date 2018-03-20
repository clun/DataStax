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

```cql
system.graph("KillrVideo").ifNotExists().create()
```

- Listing amd Describing Graph

- Dropping Graph


QUICK START
```cql
schema.config().option('graph.schema_mode').set('Development')
schema.config().option('graph.allow_scan').set('true')
```

g.V().count()



 