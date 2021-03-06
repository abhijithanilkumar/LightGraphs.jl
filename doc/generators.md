<!-- AUTOGENERATED. See 'doc/build.jl' for source. -->
# Generators

## Random Graphs
*LightGraphs.jl* implements three common random graph generators:
### erdos_renyi
```julia
erdos_renyi(n::Integer, p::Real; is_directed=false, seed=-1)
erdos_renyi(n::Integer, ne::Integer; is_directed=false, seed=-1)
```

Creates an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph with `n` vertices. Edges are added between pairs of vertices with probability `p`. Undirected graphs are created by default; use `is_directed=true` to override.

Note also that Erdős–Rényi graphs may be generated quickly using `erdos_renyi(n, ne)` or the  `Graph(nv, ne)` constructor, which randomly select `ne` edges among all the potential edges.

### watts_strogatz
```julia
watts_strogatz(n::Integer, k::Integer, β::Real)
```
Creates a [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) small model random graph with `n` vertices, each with degree `k`. Edges are randomized per the model based on probability `β`. Undirected graphs are created by default; use `is_directed=true` to override.

### random_regular_graph
```julia
random_regular_graph(n::Int, k::Int; seed=-1)
```

Creates a random undirected [regular graph](https://en.wikipedia.org/wiki/Regular_graph) with `n` vertices, each with degree `k`.

For undirected graphs, allocates an array of `nk` `Int`s, and takes approximately $nk^2$ time. For $k > n/2$, generates a graph of degree `n-k-1` and returns its complement.

### random_regular_digraph
```julia
random_regular_digraph(n::Int, k::Int; dir::Symbol=:out, seed=-1)
```

Creates a random directed [regular graph](https://en.wikipedia.org/wiki/Regular_graph) with `n` vertices, each with degree `k`. The degree (in or out) can be specified using `dir=:in` or `dir=:out`. The default is `dir=:out`.

For directed graphs, allocates an $n \times n$ sparse matrix of boolean as an adjacency matrix and uses that to generate the directed graph.

In addition, [stochastic block model](https://en.wikipedia.org/wiki/Stochastic_block_model)
graphs are available using the following constructs:
StochasticBlockModel(n,nodemap,affinities) A type capturing the parameters of the SBM. Each vertex is assigned to a block and the probability of edge (i,j) depends only on the block labels of vertex i and vertex j.

The assignement is stored in nodemap and the block affinities a k by k matrix is stored in affinities.

affinities[k,l] is the probability of an edge between any vertex in block k and any vertex in block l.

We are generating the graphs by taking random `i,j in vertices(g)` and flipping a coin with probability `affinities[nodemap[i],nodemap[j]]`.

### make_edgestream
```julia
make_edgestream(sbm::LightGraphs.StochasticBlockModel{T<:Integer,P<:Real})
```
Take an infinite sample from the sbm. Pass to `Graph(nvg, neg, edgestream)` to get a Graph object.

`StochasticBlockModel` instances may be used to create Graph objects.

## Static Graphs
*LightGraphs.jl* also implements a collection of classic graph generators:
### CompleteGraph
```julia
CompleteGraph(n::Integer)
```
Creates a complete graph with `n` vertices. A complete graph has edges connecting each pair of vertices.

### CompleteDiGraph
```julia
CompleteDiGraph(n::Integer)
```
Creates a complete digraph with `n` vertices. A complete digraph has edges connecting each pair of vertices (both an ingoing and outgoing edge).

### StarGraph
```julia
StarGraph(n::Integer)
```
Creates a star graph with `n` vertices. A star graph has a central vertex with edges to each other vertex.

### StarDiGraph
```julia
StarDiGraph(n::Integer)
```
Creates a star digraph with `n` vertices. A star digraph has a central vertex with directed edges to every other vertex.

### PathGraph
```julia
PathGraph(n::Integer)
```
Creates a path graph with `n` vertices. A path graph connects each successive vertex by a single edge.

### PathDiGraph
```julia
PathDiGraph(n::Integer)
```
Creates a path digraph with `n` vertices. A path graph connects each successive vertex by a single directed edge.

### WheelGraph
```julia
WheelGraph(n::Integer)
```
Creates a wheel graph with `n` vertices. A wheel graph is a star graph with the outer vertices connected via a closed path graph.

### WheelDiGraph
```julia
WheelDiGraph(n::Integer)
```
Creates a wheel digraph with `n` vertices. A wheel graph is a star digraph with the outer vertices connected via a closed path graph.

