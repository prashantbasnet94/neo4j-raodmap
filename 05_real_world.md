# Phase 5: Production & Ecosystem

## 1. Drivers & Connectivity
- **Node.js:** Use `neo4j-driver`. It uses the binary **Bolt** protocol (much faster than HTTP).
- **Python:** `neo4j` package.
- **Transactions:** Always use `session.executeWrite()` or `session.executeRead()` to handle retries and routing automatically.

## 2. Scaling Neo4j
- **Vertical Scaling:** Neo4j loves RAM. The "Page Cache" should ideally fit your entire graph.
- **Horizontal Scaling:** Causal Clustering.
  - **Core Servers:** Handle writes.
  - **Read Replicas:** Handle massive read volumes.

## 3. The "Polyglot" Strategy
Don't move everything to Neo4j. 
- Use **Postgres** for Transactional/Accounting data (ACID compliance on tabular data).
- Use **Neo4j** for Relationship/Insight data (Social graphs, Recommendations, Fraud).
- Sync them via CDC (Change Data Capture) or Kafka.

## 4. Final Project
Build a "Recommendation Engine" for an E-commerce site. 
- **Logic:** "Users who bought X also bought Y" (Collaborative Filtering).
- **Bonus:** Incorporate "Categories" and "Brand" for content-based filtering.
