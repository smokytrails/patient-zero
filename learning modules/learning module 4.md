LEARNING MODULE 4

## 1. Graph Theory
- in the deterministic model, we assumed that the population was homogeneously mixed
- realistically, populations don't interact uniformly
- graph theory fives us a mathematical framework for representing these relationships
- a graph is defined as

    $G = (V, E)$
- for now, let's assume the graph to be:
    - undirected
    - unweighted
    - simple
    - static

## 2. Network Metrics
- degree: $k_{avg} = 2|E| \ / \ |V|$
- clustering coefficient
- shortest path length
- connected components
- degree distribution

## 3. Network Topologies
- random network (Erdős–Rényi)
    - each possible pair of nodes is connected independently with probability $p$
    - degree distribution is generally lower, without explicitly creating hubs or local communities
- small world network (Watts–Strogatz)
    - begins with a ring lattice of local connections, then some edges are rewired to create shortcuts
    - combines local clustering with relatively short paths between distant nodes
- scale-free network (Barabási–Albert)
    - new nodes preferentially connect to existing well-connected nodes
    - produces a heterogeneous degree distribution with hubs
    - Barabási–Albert specifically is a preferential-attachment model, not a representation of every real-world scale-free network

## 4. NetworkX Functions
- random: $nx.erdos\_renyi\_graph(n, p)$
    - $n$: number of nodes
    - $p$: edge probability
- small-world: $nx.watts\_strogatz\_graph(n, k, p)$
    - $n$: number of nodes
    - $k$: initial neighbors
    - $p$: rewiring probability
- scale-free-like: $nx.barabasi\_albert\_graph(n, m)$
    - $n$: number of nodes
    - $n$: edges attached per new node

## What does and doesn't NetworkX do?
- does:
    - generating contact networks
    - accessing nodes, edges, and neighbors
    - calculating network statistics
    - identifying highly connected nodes
    - preparing network visualizations
- doesn't:
    - automatically simulate the SIR process