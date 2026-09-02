# 📚 DBMS Master Syllabus for SDE Interviews

A restructured, interview-first roadmap. Topics are grouped by **theme** rather than textbook order, moving from fundamentals → design → querying → internals → transactions → scaling, so you can study in the same sequence interviewers usually probe.

---

## 0. How to Use This Syllabus
- **Tier 1 (Must-know, asked in almost every interview):** Sections 1, 3, 4, 6, 7, 9.
- **Tier 2 (Strong SDE-2/senior signal):** Sections 5, 8, 10, 11, 12.
- **Tier 3 (System design / DB-heavy roles):** Sections 13, 14, 15.
- Practice actively writing SQL and drawing schedules/precedence graphs by hand — this is a "whiteboard" subject as much as a reading one.

---

## 1. Foundations & Architecture
*   **Core Definitions**
    *   Data vs. Database vs. DBMS vs. Database System.
    *   File System vs. DBMS — limitations of file systems (redundancy, inconsistency, isolation, integrity, security, concurrent access, atomicity).
    *   Advantages of using a DBMS.
*   **Three-Schema (ANSI-SPARC) Architecture**
    *   Physical/Internal Schema — how data is stored on disk.
    *   Logical/Conceptual Schema — what data exists and how it relates.
    *   View/External Schema — user-specific customized views.
*   **Data Independence**
    *   Physical Data Independence.
    *   Logical Data Independence.
*   **Database Languages**
    *   DDL, DML (procedural vs. declarative), DCL, TCL.
*   **DBMS Architectures**
    *   Centralized, Client-Server (2-tier vs. 3-tier), Distributed (homogeneous vs. heterogeneous).
*   **Metadata**
    *   Data Dictionary / System Catalog.
    *   Intension (schema, static) vs. Extension (instance/state, dynamic).

---

## 2. Database Design (ER Modeling)
*   **ER Model Basics**
    *   Entity, Entity Type, Entity Set.
    *   Attributes: simple vs. composite, single- vs. multi-valued, stored vs. derived, null.
    *   Key Attributes: candidate key, primary key.
*   **Weak Entities**
    *   Identifying (owner) entity set, partial key/discriminator, identifying relationship.
*   **Relationships & Constraints**
    *   Degree: unary, binary, ternary, n-ary.
    *   Cardinality ratios: 1:1, 1:N, M:N.
    *   Participation: total (existential dependency) vs. partial.
*   **Enhanced ER (EER)**
    *   Specialization & Generalization.
    *   Aggregation.
    *   Attribute Inheritance.
*   **Applied Schema Design**
    *   Choosing primary/foreign keys.
    *   **Surrogate vs. Natural Keys** — trade-offs (stability, size, index performance vs. semantic meaning).
    *   Normalization vs. Denormalization trade-off (write efficiency vs. read performance).
    *   Practice designing real systems: e-commerce, ride-sharing, social media, URL shortener, booking system.

---

## 3. Constraints & Referential Integrity
*   **Key Constraints**
    *   `PRIMARY KEY`, `UNIQUE`, `FOREIGN KEY`.
*   **Domain/Attribute Constraints**
    *   `NOT NULL`, `CHECK`, `DEFAULT`.
*   **Referential Actions** (on update/delete of a referenced key)
    *   `CASCADE`, `SET NULL`, `SET DEFAULT`, `RESTRICT` / `NO ACTION`.

---

## 4. Relational Model, Algebra & Calculus
*   **Relational Model**
    *   Relation, Domain, Tuple, Attribute, Degree (arity), Cardinality.
    *   Integrity constraints: domain, key, entity, referential.
*   **Keys**
    *   Super Key, Candidate Key, Primary Key, Alternate Key, Composite Key, Foreign Key.
*   **Relational Algebra**
    *   Unary: Selection (σ), Projection (π), Rename (ρ).
    *   Set-based: Union (∪), Intersection (∩), Difference (−), Cartesian Product (×).
    *   Joins: Theta Join, Equi-Join, Natural Join, Outer Joins (Left/Right/Full), Semi-Join, Anti-Join.
    *   Division (÷).
*   **Relational Calculus**
    *   Tuple Relational Calculus (TRC), Domain Relational Calculus (DRC), safe expressions.

---

## 5. Functional Dependencies & Normalization
*   **Functional Dependencies**
    *   Definition (X → Y), trivial vs. non-trivial.
    *   Armstrong's Axioms: reflexivity, augmentation, transitivity.
    *   Derived rules: union, decomposition, pseudo-transitivity.
    *   Attribute Closure (X⁺) and finding candidate keys.
    *   Canonical Cover / Minimal Cover.
*   **Normal Forms**
    *   Anomalies: insertion, deletion, update.
    *   1NF — atomic values, no repeating groups.
    *   2NF — 1NF + no partial dependency.
    *   3NF — 2NF + no transitive dependency.
    *   BCNF — every determinant is a super key.
    *   4NF (multi-valued dependencies), 5NF (join dependencies).
*   **Decomposition Properties**
    *   Lossless-join decomposition.
    *   Dependency preservation.

---

## 6. SQL for Interviews
> *Practice writing these, not just reading them — use a scratch DB (SQLite/Postgres) alongside this section.*
*   **Syntax Layers**
    *   DDL: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`.
    *   DML: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
*   **Query Mechanics**
    *   Logical order of execution (`FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT`).
    *   Operators: comparison, logical, `BETWEEN`, `IN`, `LIKE`, `IS NULL`.
    *   Three-valued logic: `TRUE` / `FALSE` / `UNKNOWN` and how `NULL` interacts with it.
*   **Aggregation**
    *   `GROUP BY`, `HAVING` vs. `WHERE`, aggregate functions (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`).
*   **Joins in Practice**
    *   Inner, Left/Right/Full Outer, Self Join, Cross Join.
    *   Common join pitfalls (fan-out rows, duplicate counting).
*   **Subqueries & CTEs**
    *   Correlated vs. non-correlated subqueries.
    *   Common Table Expressions (`WITH`), recursive CTEs.
    *   Subquery vs. Join vs. CTE — when to use which.
*   **Window Functions**
    *   `ROW_NUMBER`, `RANK`, `DENSE_RANK`.
    *   `LEAD`/`LAG`, running totals, moving averages.
    *   `PARTITION BY` vs. `GROUP BY`.
*   **Views**
    *   Virtual Views vs. Materialized Views (refresh strategies).
*   **Set Operations**
    *   `UNION` vs. `UNION ALL`, `INTERSECT`, `EXCEPT`/`MINUS`.
*   **Classic Interview SQL Patterns**
    *   Nth highest salary, duplicate detection, gaps-and-islands, running totals, top-N per group, pivoting.

---

## 7. Transactions & Concurrency Control (Core Theory)
*   **Transaction Basics**
    *   Definition, states (Active, Partially Committed, Committed, Failed, Aborted).
    *   **ACID:** Atomicity, Consistency, Isolation, Durability.
*   **Schedules & Serializability**
    *   Serial vs. concurrent schedules.
    *   Conflict Serializability — conflicting operations, precedence graph, cycle detection.
    *   View Serializability — blind writes.
    *   Recoverability: recoverable, cascadeless, strict schedules.
*   **Concurrency Anomalies**
    *   Dirty Read, Non-Repeatable Read, Phantom Read, Lost Update.
*   **Isolation Levels**
    *   Read Uncommitted, Read Committed, Repeatable Read, Serializable — which anomalies each prevents.
*   **Locking in Practice**
    *   Granularity: row, page, table.
    *   Shared (S) vs. Exclusive (X) locks, compatibility matrix.
    *   Lock escalation.
    *   Optimistic (version/timestamp check) vs. Pessimistic (`SELECT ... FOR UPDATE`) locking.
*   **Concurrency Control Protocols**
    *   Two-Phase Locking (2PL), Strict 2PL, Rigorous 2PL.
    *   Timestamp Ordering & Thomas' Write Rule.
    *   **MVCC** — multiple row versions so readers don't block writers (Postgres, MySQL InnoDB).
*   **Deadlocks**
    *   Detection (Wait-For Graph), Prevention (Wait-Die, Wound-Wait), Recovery (victim selection).

---

## 8. Transactions in Application Code
*   **Lifecycle Commands**
    *   `BEGIN`/`START TRANSACTION`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`.
*   **Transaction Boundaries**
    *   Where a transaction should start/end in app code; ORM patterns (`@Transactional`, unit-of-work).
*   **Long-Running Transaction Anti-Patterns**
    *   Extended lock hold times → concurrency blockages.
    *   Connection pool starvation.
    *   Undo/log bloat, delayed MVCC cleanup.
    *   Increased deadlock risk.
    *   Best practice: keep transactions short; never make network calls (e.g., payment gateway) inside a DB transaction.
*   **Distributed Transactions** *(Tier 3, but increasingly asked)*
    *   Two-Phase Commit (2PC) — coordinator/participant protocol, blocking problem.
    *   Saga Pattern — choreography vs. orchestration, compensating transactions.
    *   Idempotency keys for safe retries.

---

## 9. Storage, Indexing & Query Optimization
*   **Storage Fundamentals**
    *   Buffer pool, replacement policies (LRU), dirty pages.
    *   RAID levels: RAID 0, 1, 5, 10.
*   **Indexing Mechanics**
    *   Dense vs. sparse indexes.
    *   Clustered vs. non-clustered indexes.
    *   B-Tree vs. B+ Tree (node fan-out, leaf-linked range scans).
    *   Hash indexes (equality-only, no range scans).
*   **Practical Indexing**
    *   When indexes help: selective filters, sorts, joins.
    *   Composite indexes & the **leftmost-prefix rule**.
    *   **Covering indexes** — index-only scans.
    *   **Selectivity & cardinality** — high-selectivity vs. low-selectivity columns.
    *   When an index hurts: small tables, low selectivity, write-heavy columns (index maintenance cost).
*   **Query Optimization**
    *   Reading `EXPLAIN` / execution plans.
    *   Access paths: sequential scan, index scan, index seek.
    *   Join strategies: Nested Loop, Hash Join, Sort-Merge Join — when each wins.
    *   Common slow-query causes: missing indexes, N+1 queries, leading-wildcard `LIKE '%x'`, unindexed `ORDER BY`, bad join order, implicit type casts.

---

## 10. Recovery & Durability
*   **Log-Based Recovery**
    *   Write-Ahead Logging (WAL) protocol.
    *   Undo and Redo operations.
    *   Deferred vs. Immediate modification.
*   **Checkpoints**
    *   How checkpointing bounds recovery time.
*   **Shadow Paging** (alternative to log-based recovery).

---

## 11. Caching, Connection Pooling & Latency
*   **Why Cache in Front of a DB**
    *   Offloading read load; nanosecond memory access vs. millisecond disk access.
*   **Caching Patterns**
    *   Cache-Aside (Lazy Loading).
    *   Write-Through.
    *   Write-Behind / Write-Back.
*   **Cache Invalidation**
    *   TTL expiration, write-invalidation.
    *   The classic hard problem: "cache invalidation and naming things."
*   **Redis as a DB-adjacent Cache**
    *   Common structures: Strings, Hashes, Sorted Sets, Lists.
*   **Connection Pooling**
    *   Why pools exist: TCP handshake + TLS + backend process spawn cost per connection.
    *   Mechanism: checkout/return cycle.
    *   Pool-size tuning: too small → request queueing; too large → backend resource/context-switch exhaustion.

---

## 12. Security & Administration *(often skipped, occasionally asked)*
*   **Access Control**
    *   `GRANT` / `REVOKE`, roles vs. users, principle of least privilege.
*   **SQL Injection**
    *   Root cause, parameterized queries / prepared statements as the fix.
*   **Encryption**
    *   At-rest vs. in-transit encryption; column-level encryption trade-offs.
*   **Auditing & Backups**
    *   Full vs. incremental vs. differential backups; point-in-time recovery.

---

## 13. OLTP vs. OLAP & Data Warehousing *(Tier 3)*
*   **OLTP vs. OLAP**
    *   Transactional workloads vs. analytical workloads — differing access patterns and schema design goals.
*   **Data Warehouse Schema Design**
    *   Star Schema (fact + dimension tables) vs. Snowflake Schema (normalized dimensions).
    *   Fact tables, dimension tables, slowly changing dimensions (SCD Types 1/2/3).
*   **ETL/ELT Basics**
    *   Extract-Transform-Load vs. Extract-Load-Transform; batch vs. streaming ingestion.

---

## 14. SQL vs. NoSQL & Data Models *(Tier 3)*
*   **Relational vs. Non-Relational Paradigms**
    *   When relational modeling wins vs. when it becomes a bottleneck.
*   **NoSQL Categories**
    *   Key-Value stores (Redis, DynamoDB).
    *   Document stores (MongoDB) — schema flexibility, embedding vs. referencing.
    *   Wide-Column stores (Cassandra, HBase) — partition key + clustering key design.
    *   Graph databases (Neo4j) — when relationships are the primary query pattern.
*   **Modeling Trade-offs**
    *   Embedding vs. referencing, denormalization-by-default in NoSQL, query-first schema design.

---

## 15. Scaling, Replication & Distributed Data *(System Design Track)*
*   **Scaling Strategies**
    *   Vertical vs. horizontal scaling.
*   **Replication**
    *   Primary-Replica (Leader-Follower): writes to primary, reads scaled across replicas.
    *   Synchronous vs. Asynchronous replication — consistency/latency/availability trade-offs.
    *   Replication lag and "read-your-own-writes" inconsistency.
    *   Failover — promoting a replica to primary.
    *   Multi-leader and leaderless (quorum-based) replication, at a conceptual level.
*   **Partitioning / Sharding**
    *   Horizontal partitioning across physical nodes via a shard key.
    *   Range sharding, Hash sharding, Directory-based sharding — trade-offs (hot spots, rebalancing cost, range-query support).
    *   Resharding strategies (consistent hashing to minimize data movement).
*   **Consistency Models & Theorems**
    *   CAP Theorem (Consistency, Availability, Partition tolerance — pick 2 under a partition).
    *   PACELC Theorem (extends CAP with the latency/consistency trade-off absent a partition).
    *   Strong vs. Eventual vs. Causal consistency.
*   **Distributed Query Concepts**
    *   Distributed joins and their cost; scatter-gather queries; cross-shard transactions (why they're expensive — ties back to 2PC in Section 8).

---

## Appendix: Fast Interview Recall Checklist
- [ ] Explain ACID with a real example (e.g., bank transfer).
- [ ] Draw a precedence graph and detect a cycle for conflict serializability.
- [ ] Name which isolation level stops which anomaly.
- [ ] Explain leftmost-prefix rule with a 3-column composite index example.
- [ ] Explain clustered vs. non-clustered index with a concrete table.
- [ ] Walk through normalizing an unnormalized table to 3NF/BCNF.
- [ ] Explain optimistic vs. pessimistic locking with a use case each.
- [ ] Explain replication lag and one strategy to mitigate it.
- [ ] Explain CAP theorem with a real system example (e.g., DynamoDB = AP, traditional RDBMS = CP).
- [ ] Write a query for "Nth highest value per group" using window functions.
- [ ] Explain cache-aside vs. write-through vs. write-behind with failure-mode trade-offs.
- [ ] Explain why long transactions are dangerous in production.
