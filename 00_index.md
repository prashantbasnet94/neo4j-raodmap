# Neo4j Master Architect Roadmap

This roadmap is specifically designed for an expert in Relational (Postgres) and Document (Mongoose) databases to master the Graph paradigm.

## Phases

### [Phase 1: Foundations & The Graph Mindset](./01_foundations.md)
- Property Graph Model vs. SQL/NoSQL.
- Cypher Syntax & Index-free Adjacency.
- CRUD operations in Graph.

### [Phase 2: Advanced Data Modeling](./02_modeling.md)
- Refactoring Relational schemas to Graph.
- Labels vs. Properties.
- Handling Many-to-Many without Join Tables.

### [Phase 3: Cypher Query Optimization](./03_advanced_cypher.md)
- `EXPLAIN` and `PROFILE`.
- Understanding the Bolt protocol.
- Indexing strategies (B-Tree, Full-text, Point).

### [Phase 4: Graph Data Science (GDS) & Algorithms](./04_gds.md)
- Pathfinding (Dijkstra, A*).
- Centrality (PageRank).
- Community Detection (Louvain, Label Propagation).

### [Phase 5: Production Architecture](./05_real_world.md)
- Neo4j Aura vs. Self-hosted.
- Integration with Node.js/Python.
- Security and Role-Based Access Control (RBAC).

### [Phase 6: Selection Criteria & Polyglot Design](./06_selection_criteria.md)
- When to use Neo4j vs. SQL vs. NoSQL.
- Designing Polyglot systems.
- Syncing strategies (CDC/Kafka).

### [Phase 7: The "Shadow Side" - Downsides & Limitations](./07_downsides_and_limitations.md)
- The RAM Tax and Memory Management.
- The Supernode Problem.
- Write Throughput vs. Read Speed.
