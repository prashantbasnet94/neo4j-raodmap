# Phase 6: Selection Criteria & Polyglot Design

## 1. When to NOT use Neo4j
- **Log Data:** Use ElasticSearch or ClickHouse.
- **Simple Web Content:** Use MongoDB or Postgres.
- **Strict Financial Ledgers:** Use Postgres (for the ACID-heavy transactional integrity).

## 2. The Polyglot Architecture
In the top 1% of apps, Neo4j rarely lives alone.

### Scenario: E-Commerce
1. **Postgres:** Stores `Users`, `Orders`, and `Inventory`. (Transactional Truth)
2. **Neo4j:** Stores `User -[:BOUGHT]-> Product` and `Product -[:IN_CATEGORY]-> Category`. (Recommendation Engine)
3. **Sync Strategy:** Use a Message Queue (Kafka/RabbitMQ). When an order is placed in Postgres, send a message to Neo4j to create the `:BOUGHT` relationship.

## 3. Challenge: The "Architect's Choice"
You are building a **Social Media Platform**. 
- Where do you store the **User Profiles**?
- Where do you store the **Follower Graph**?
- Where do you store the **Post Content/Comments**?

**1% Answer:**
- **Profiles:** Postgres (Searchable, rigid).
- **Followers:** Neo4j (Deep traversal for "People you may know").
- **Posts:** MongoDB (Highly nested, document-based structure).
