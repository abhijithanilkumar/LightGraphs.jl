<!-- AUTOGENERATED. See 'doc/build.jl' for source. -->
# Basic Functions

The following basic measures have been implemented for `Graph` and `DiGraph`
types:

## Vertices and Edges
### vertices
```julia
vertices(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
```
Return the vertices of a graph.

### edges
```julia
edges(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
```
Return an iterator to the edges of a graph. The returned iterator is valid for one pass over the edges, and is invalidated by changes to `g`.

### is_directed
```julia
is_directed(g::LightGraphs.DiGraph)
is_directed(g::LightGraphs.Graph)
```
Returns `true` if `g` is a `DiGraph`.

### nv
```julia
nv(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
```
The number of vertices in `g`.

### ne
```julia
ne(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
```
The number of edges in `g`.

### has_edge
```julia
has_edge(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, src::Int64, dst::Int64)
has_edge(g::LightGraphs.DiGraph, e::Pair{Int64,Int64})
has_edge(g::LightGraphs.Graph, e::Pair{Int64,Int64})
```
Return true if the graph `g` has an edge from `src` to `dst`.

### has_vertex
```julia
has_vertex(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
```
Return true if `v` is a vertex of `g`.

### in_edges
```julia
in_edges(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
```
Return an Array of the edges in `g` that arrive at vertex `v`.

### out_edges
```julia
out_edges(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
```
Return an Array of the edges in `g` that emanate from vertex `v`.

### src
```julia
src(e::Pair{Int64,Int64})
```
Return source of an edge.

### dst
```julia
dst(e::Pair{Int64,Int64})
```
Return destination of an edge.

### reverse
```julia
reverse(g::DiGraph)
```

Produces a graph where all edges are reversed from the original.

## Neighbors and Degree
### degree
```julia
degree(g::LightGraphs.DiGraph, v::Int64)
degree(g::LightGraphs.Graph, v::Int64)
degree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
degree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::AbstractArray{Int64,1})
```
Return the number of edges (both ingoing and outgoing) from the vertex `v`.

### indegree
```julia
indegree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
indegree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
indegree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::AbstractArray{Int64,1})
```
Return the number of edges which start at vertex `v`.

### outdegree
```julia
outdegree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
outdegree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
outdegree(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::AbstractArray{Int64,1})
```
Return the number of edges which end at vertex `v`.

### Δ
```julia
Δ(g)
```
Return the maximum `degree` of vertices in `g`.

### δ
```julia
δ(g)
```
Return the minimum `degree` of vertices in `g`.

### Δout
```julia
Δout(g)
```
Return the maxium `outdegree` of vertices in `g`.

### δout
```julia
δout(g)
```
Return the minimum `outdegree` of vertices in `g`.

### δin
```julia
δin(g)
```
Return the maximum `indegree` of vertices in `g`.

### Δin
```julia
Δin(g)
```
Return the minimum `indegree` of vertices in `g`.

### degree_histogram
```julia
degree_histogram(g::Union{LightGraphs.DiGraph,LightGraphs.Graph})
```
Produces a histogram of degree values across all vertices for the graph `g`. The number of histogram buckets is based on the number of vertices in `g`.

### density
```julia
density(g::LightGraphs.DiGraph)
density(g::LightGraphs.Graph)
```
Density is defined as the ratio of the number of actual edges to the number of possible edges. This is $|v| |v-1|$ for directed graphs and $(|v| |v-1|) / 2$ for undirected graphs.

### neighbors
```julia
neighbors(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
```
Returns a list of all neighbors of vertex `v` in `g`.

For DiGraphs, this is equivalent to `out_neighbors(g, v)`.

NOTE: returns a reference, not a copy. Do not modify result.

### in_neighbors
```julia
in_neighbors(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, v::Int64)
```
Returns a list of all neighbors connected to vertex `v` by an incoming edge.

NOTE: returns a reference, not a copy. Do not modify result.

### all_neighbors
```julia
all_neighbors(g::LightGraphs.DiGraph, v::Int64)
```
Returns all the vertices which share an edge with `v`.

### common_neighbors
```julia
common_neighbors(g::Union{LightGraphs.DiGraph,LightGraphs.Graph}, u::Int64, v::Int64)
```
Returns the neighbors common to vertices `u` and `v` in `g`.

