# Problem 1

---

### Algorithm Description
The goal is to compute the equivalent resistance between two nodes (say, a source and a sink) in a circuit represented as an undirected graph. In this graph:

- **Nodes** represent junctions or connection points.

- **Edges** represent resistors, with weights equal to their resistance values (in ohms).

The algorithm iteratively simplifies the graph by identifying and reducing **series** and **parallel** resistor configurations until only two nodes remain, connected by a single equivalent resistance. Here’s how it works:

1. **Identify Series Connections**: 
-Two resistors are in series if they share a node with a degree of 2 (i.e., the node connects only to the two resistors). Replace them with a single resistor whose resistance is the sum of the two.

2. **Identify Parallel Connections**: 
-Two resistors are in parallel if they connect the same pair of nodes. Replace them with a single resistor whose resistance is computed using the parallel formula: $R_{eq} = \frac{R_1 \cdot R_2}{R_1 + R_2}$ (or equivalently, $\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}$).

3. **Iterate**: 
-Repeat the process, updating the graph after each reduction, until no further series or parallel simplifications are possible. For complex graphs, this may leave a reduced structure that requires additional techniques (e.g., delta-wye transformations), but we’ll focus on circuits reducible by series and parallel rules.

4. **Termination**: 
-Stop when the graph consists of just two nodes connected by one edge, where the edge weight is the equivalent resistance.

To handle **nested combinations**, the algorithm processes the graph iteratively, reducing innermost series or parallel structures first. A traversal method (like DFS) can help detect these patterns systematically.

---

[Equivalent Resistance Using Graph Theory](Equivalent_Resistance_Using_Graph_Theory.html)

[circuits_sim](circuitssim.html)

**Explanation**:
- **Series Detection**: A node with degree 2 indicates a chain. We sum the resistances and bypass the intermediate node.
- **Parallel Detection**: Multiple edges between two nodes are combined using the parallel formula.
- **Nested Handling**: The while loop ensures iterative reduction. Inner structures (e.g., a series pair within a parallel set) are simplified in subsequent iterations as the graph updates.

---

### Example Applications

#### Example 1: Simple Series Combination
- **Circuit**: Two resistors, $R_1 = 2 \, \Omega$ and $R_2 = 3 \, \Omega$, in series between nodes A and B (via node C).
- **Graph**: A --(2)--> C --(3)--> B
- **Step 1**: Node C has degree 2. Reduce series: $R_{eq} = 2 + 3 = 5 \, \Omega$.
- **Resulting Graph**: A --(5)--> B
- **Output**: $5 \, \Omega$

#### Example 2: Simple Parallel Combination
- **Circuit**: Two resistors, $R_1 = 4 \, \Omega$ and $R_2 = 6 \, \Omega$, in parallel between nodes A and B.
- **Graph**: A --(4)--> B, A --(6)--> B
- **Step 1**: Two edges between A and B. Reduce parallel: $R_{eq} = \frac{4 \cdot 6}{4 + 6} = \frac{24}{10} = 2.4 \, \Omega$.
- **Resulting Graph**: A --(2.4)--> B
- **Output**: $2.4 \, \Omega$

#### Example 3: Nested Configuration
- **Circuit**: $R_1 = 2 \, \Omega$ and $R_2 = 3 \, \Omega$ in series, then in parallel with $R_3 = 5 \, \Omega$, between A and B.
- **Graph**: 
  - A --(2)--> C --(3)--> B (series path)
  - A --(5)--> B (parallel resistor)
- **Step 1**: Node C has degree 2. Series reduction: $R_{series} = 2 + 3 = 5 \, \Omega$. New graph: A --(5)--> B, A --(5)--> B.
- **Step 2**: Two edges between A and B. Parallel reduction: $R_{eq} = \frac{5 \cdot 5}{5 + 5} = \frac{25}{10} = 2.5 \, \Omega$.
- **Resulting Graph**: A --(2.5)--> B
- **Output**: $2.5 \, \Omega$

---

### Efficiency and Improvements

- **Time Complexity**: Depends on graph size and structure. For $n$ nodes and $e$ edges, each iteration scans nodes ($O(n)$) and edges ($O(e)$), with potentially $O(n)$ iterations, yielding $O(n \cdot (n + e))$ in the worst case. Parallel detection may require $O(e^2)$ if checking all node pairs naively.
- **Improvements**:
  - Use adjacency lists for efficient neighbor lookup.
  - Prioritize reductions (e.g., series before parallel) based on graph traversal.
  - For non-reducible graphs (e.g., bridges or cycles), integrate delta-wye transformations or Kirchhoff’s laws.
  - Leverage libraries like NetworkX for optimized graph operations.

This approach scales well for circuits reducible by series and parallel rules and provides a clear, systematic way to handle nested configurations. For truly complex graphs, additional techniques would enhance its robustness.
