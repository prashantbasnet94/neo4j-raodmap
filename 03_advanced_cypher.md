# Phase 3: Cypher Query Optimization

## 1. The Postgres Equivalent: EXPLAIN ANALYZE
In Neo4j, we use `EXPLAIN` (plan without running) and `PROFILE` (plan with execution stats).

**Key Metrics:**
- **DbHits:** The number of times the engine interacts with the storage layer. Your goal is to minimize this.
- **Rows:** The number of records passed between operators.

## 2. Avoiding Eager Aggregation
A common performance killer is performing a `count()` too early in a query, which forces the engine to materialize results before it needs to.

**Bad:**
```cypher
MATCH (u:User)-[:FOLLOWS]->(f)
WITH u, count(f) as count
MATCH (u)-[:MEMBER_OF]->(g)
RETURN u, count, g
```

**Good:** Use subqueries or pattern comprehensions to keep the main row count low.

## 3. Indexing Strategies
Neo4j isn't "Schemaless"; it's "Schema-lite."
- **Range Indexes:** Standard B-Tree for equality and range.
- **Text Indexes:** For fuzzy matching.
- **Point Indexes:** For geospatial queries.

## 4. Optimization Challenge
You have a query that finds all "Common Friends" between two users but it's taking 5 seconds on 1M nodes. 
**Investigate:** Use `PROFILE`. Are you seeing a `CartesianProduct` operator? How do you use `USING INDEX` to force a starting point?
