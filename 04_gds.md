# Phase 4: Graph Data Science (GDS)

## 1. The LeetCode Bridge
| Algorithm | LeetCode Pattern | GDS Application |
| :--- | :--- | :--- |
| **BFS/DFS** | Level Order / Path finding | Shortest Path, Reachability |
| **Dijkstra** | Cheapest Path | Logistics, Network Routing |
| **Tarjan's** | Strongly Connected Components | Fraud Rings, Community Detection |
| **PageRank** | In-degree Centrality | Influencer Score, Search Ranking |

## 2. The GDS Workflow
1. **Project a Graph:** Move data from the database into a high-performance in-memory graph.
   ```cypher
   CALL gds.graph.project('myGraph', 'User', 'FOLLOWS')
   ```
2. **Run Algorithm:** Execute the math.
   ```cypher
   CALL gds.pageRank.stream('myGraph')
   YIELD nodeId, score
   ```
3. **Write Back:** Save the results to the nodes as properties.

## 3. Real-world Use Case: Fraud Detection
If User A, B, and C all share the same Credit Card node and IP node, they form a "Synthetic Identity" ring. 
**GDS Tool:** Weakly Connected Components (WCC).

## 4. Challenge
Translate the "Word Ladder" LeetCode problem into a Cypher query. If every node is a `Word` and a relationship `[:DIFFERS_BY_ONE]` exists, how do you find the shortest transformation sequence from "HIT" to "COG"?
