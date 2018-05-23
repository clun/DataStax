```sql
// --------------
// ---- Graoh ---
// --------------

system.graph("KillrVideo").
         option("graph.replication_config").
         set("{'class' : 'NetworkTopologyStrategy','DC-East' : 3,'DC-West' : 5}").
         option("graph.system_replication_config").
         set("{'class' : 'NetworkTopologyStrategy','DC-East' : 3,'DC-West' : 3}").
       ifNotExists().create()

system.graph("KillrVideo").exists()
system.graph("KillrVideo").describe()
system.graphs()
system.describe()

// -----------------
// ---- Vertices ---
// -----------------

system.graph("MyOtherGraph").drop()

// Properties
schema.propertyKey("year").Int().single().create();
// single() is assumed by default and can be omitted
schema.propertyKey("year").Int().create();
// Vertices only
schema.propertyKey("production").Text().multiple().create();
// Meta
schema.propertyKey("budget").Text().multiple().properties("source","date").create();

schema.vertexLabel("user").describe()

// --------------
// ---- Egdes ---
// --------------

schema.edgeLabel("rated").
       single().
       properties("rating").
       connection("user","movie").
       create();

// Multiple by default
schema.edgeLabel("actor").
       multiple().
       connection("movie","person").
       create();

// Multi connection
schema.edgeLabel("knows").
       single().
       connection("user","user").
       connection("user","person").
       connection("person","user").
       create();

schema.edgeLabel("rated").describe()

// ----------------
// ---- Indices ---
// ----------------
Vertex, Properties and Edges


Default VERTEXID or CUSTOM VERTEX ID
EdgeId generated automatically

g.V().hasId("{~label=movie, member_id=0, community_id=63341568}")
Indexed properties to query the graph

Custom vertex ID
schema.vertexLabel("user").
       partitionKey("username").
       properties("age","gender").create();

schema.vertexLabel("movie").
       partitionKey("year","country").
       clusteringKey("movieId").
       properties("title","duration").create();

// Custom ID for data retrieval
g.V().hasId("{country=United States, movieId=m267, ~label=movie, year=2010}")


Vertex u = g.V().addVertex("user");
       u.property("userId","u2016");
       u.property("age",36);
       u.property("gender","M");
```




