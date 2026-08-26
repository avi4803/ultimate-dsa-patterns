# 📚 The Master DBMS Syllabus for SDE Interviews

---

## 1. Introduction, Architecture & Foundational Concepts
*   **Basic Definitions**
    *   What is Data, Database, DBMS, and Database System?
    *   File System vs. DBMS (Limitations of File Systems: redundancy, inconsistency, isolation, security, concurrent access).
    *   Advantages of using a DBMS.
*   **Three-Schema (ANSI-SPARC) Architecture & Data Abstraction**
    *   Physical Level (Internal Schema) — *How* data is physically stored on disk.
    *   Logical/Conceptual Level (Conceptual Schema) — *What* data is stored and what relationships exist.
    *   View Level (External Schema) — *Who* sees what (user-specific customized views).
*   **Data Independence**
    *   Physical Data Independence (changing physical storage without affecting logical schema).
    *   Logical Data Independence (changing logical schema without affecting views/application programs).
*   **Database Languages**
    *   DDL (Data Definition Language)
    *   DML (Data Manipulation Language) — Procedural vs. Non-procedural (Declarative)
    *   DCL (Data Control Language)
    *   TCL (Transaction Control Language)
*   **DBMS Architectures**
    *   Centralized Database Systems
    *   Client-Server Architectures (2-tier vs. 3-tier)
    *   Distributed Database Systems (Homogeneous vs. Heterogeneous)
*   **Metadata & Database Instance**
    *   Data Dictionary / Catalog (Metadata storage)
    *   Intension (Database Schema — structural metadata, static)
    *   Extension (Database State/Instance — actual data at a given moment, dynamic)

---

## 2. Database Design & Schema Design
*   **ER Model Concepts**
    *   **Entity, Entity Type, Entity Set**
    *   Attributes (Simple vs. Composite, Single-valued vs. Multi-valued, Stored vs. Derived, Null attributes)
    *   Key Attributes (Candidate, Primary)
    *   **Weak Entity Sets:** Identifying Entity Set (Owner), Partial Key (Discriminator), Identifying Relationship (double diamond).
*   **Relationships & Constraints**
    *   Degree of Relationship (Unary, Binary, Ternary, N-ary)
    *   Cardinality Ratios & Mapping Constraints (One-to-One, One-to-Many, Many-to-Many)
    *   Participation Constraints (Total Participation/Existential dependency vs. Partial Participation)
*   **Enhanced ER (EER) Diagrams**
    *   Specialization and Generalization
    *   Aggregation
    *   Attribute Inheritance
*   **Schema Design Best Practices**
    *   Choosing Primary and Foreign keys.
    *   **Surrogate vs. Natural Keys:**
        *   *Natural Keys:* Attributes that naturally exist and are unique (e.g., SSN, Email).
        *   *Surrogate Keys:* System-generated, artificial unique identifiers (e.g., auto-incrementing integers, UUIDs). Pros and cons of each.
    *   Normalization vs. Denormalization (balancing write efficiency vs. read performance).
    *   Designing production schemas for common applications (e.g., E-Commerce, Ride-Sharing, Social Media).

---

## 3. Database Constraints & Referential Actions
*   **Key Constraints**
    *   `PRIMARY KEY` (Uniquely identifies rows, cannot contain NULLs).
    *   `UNIQUE` (Ensures all values in a column are distinct, can contain NULLs).
    *   `FOREIGN KEY` (Enforces referential integrity between tables).
*   **Domain & Attribute Constraints**
    *   `NOT NULL` (Prevents inserting NULL values).
    *   `CHECK` (Ensures values in a column meet a specific boolean condition).
    *   `DEFAULT` (Provides default fallback values).
*   **Referential Integrity & Actions**
    *   How the database reacts when a referenced primary key is updated or deleted:
        *   `CASCADE` (Propagates updates/deletions automatically to child tables).
        *   `SET NULL` (Sets child foreign key fields to NULL when parent is deleted/updated).
        *   `RESTRICT` / `NO ACTION` (Rejects the deletion/update of the parent key if child rows depend on it).

---

## 4. The Relational Model & Relational Algebra
*   **Relational Model Concepts**
    *   Relation, Domain, Tuple, Attribute, Degree (Arity), Cardinality.
    *   Relational Integrity Constraints (Domain, Key, Entity Integrity, Referential Integrity).
*   **Keys in DBMS**
    *   Super Key, Candidate Key, Primary Key, Alternate/Secondary Key, Foreign Key, Composite Key.
*   **Relational Algebra Operations**
    *   **Unary:** Selection ($\sigma$), Projection ($\pi$), Rename ($\rho$).
    *   **Binary/Set:** Union ($\cup$), Intersection ($\cap$), Set Difference ($-$), Cartesian Product ($\times$).
    *   **Joins:** Theta Join ($\bowtie_\theta$), Equi-Join, Natural Join ($\bowtie$), Outer Joins (Left Outer $\rtimes$, Right Outer $\ltimes$, Full Outer $\bowtie$), Semi-Join, Anti-Join.
    *   **Division Operation ($/$)**
*   **Relational Calculus**
    *   Tuple Relational Calculus (TRC)
    *   Domain Relational Calculus (DRC)
    *   Safe expressions

---

## 5. Schema Design & Normalization
*   **Functional Dependencies (FD)**
    *   Definition ($X \rightarrow Y$), Trivial vs. Non-trivial FDs.
    *   Armstrong's Axioms (Reflexivity, Augmentation, Transitivity).
    *   Derived Rules (Union, Decomposition, Pseudo-transitivity).
    *   Attribute Closure ($X^+$) and finding Candidate Keys.
    *   Canonical Cover / Minimal Cover.
*   **Normalization Theory**
    *   Design Anomalies (Insertion, Deletion, Modification).
    *   **First Normal Form (1NF):** Atomic values, no multi-valued attributes.
    *   **Second Normal Form (2NF):** 1NF + no partial dependency.
    *   **Third Normal Form (3NF):** 2NF + no transitive dependency.
    *   **Boyce-Codd Normal Form (BCNF):** Strict condition ($X \rightarrow Y$ requires $X$ to be a super key).
    *   **Fourth Normal Form (4NF) & Fifth Normal Form (5NF).**
*   **Properties of Decomposition**
    *   Lossless Join Decomposition.
    *   Dependency Preservation.

---

## 6. Structured Query Language (SQL)
*   *Refer to the [SQL.md](file:///c:/Backend/InterViewReady/Database/SQL.md) file for query templates and practice patterns.*
*   **Standard Topics covered:**
    *   DDL & DML syntax.
    *   SQL Operators & Logical Execution Order.
    *   Aggregations, Subqueries, and CTEs.
    *   Views (Virtual) vs. Materialized Views.
    *   Window Functions & Partitioning.
    *   Three-valued NULL Logic.

---

## 7. Transactions & Concurrency Control (Deep Core)
*   **Transactions Basics**
    *   Definition, States (Active, Partially Committed, Committed, Failed, Aborted).
    *   **ACID Properties** (Atomicity, Consistency, Isolation, Durability).
*   **Schedules & Serializability**
    *   Serial vs. Concurrent Schedules.
    *   **Conflict Serializability:** Conflicting Operations, Precedence Graph (Cycle detection).
    *   **View Serializability:** Blind writes.
    *   Recoverability (Recoverable, Cascadeless, Strict schedules).
*   **Concurrency Anomalies**
    *   **Dirty Read (Read Uncommitted Data):** Transaction reads updates from an uncommitted transaction.
    *   **Non-Repeatable Read (Inconsistent Analysis):** Consecutive reads of the same row return different values.
    *   **Phantom Read:** Consecutive range queries return different sets of rows (newly inserted/deleted rows).
    *   **Lost Update:** Two transactions concurrently update the same data, and one overrides the other's changes.
*   **Transaction Isolation Levels**
    *   **Read Uncommitted:** No read locks, allows all anomalies.
    *   **Read Committed:** Prevents Dirty Reads. Shared locks released immediately after read.
    *   **Repeatable Read:** Prevents Dirty and Non-Repeatable Reads. Shared locks held until transaction completes.
    *   **Serializable:** Prevents all anomalies including Phantom Reads (often via Range Locks / Index Locks).
*   **Database Locks in Practice**
    *   **Granularity:** Row-level vs. Page-level vs. Table-level locks.
    *   **Lock Modes:** Shared (S) vs. Exclusive (X) locks (Compatibility Matrix).
    *   **Lock Escalation:** Automatically converting many fine-grained locks (row-level) into a coarser lock (table-level) to save memory/resources.
    *   **Optimistic vs. Pessimistic Locking:**
        *   *Pessimistic:* Lock resources preemptively (uses SELECT ... FOR UPDATE). Good for high conflict.
        *   *Optimistic:* Allow concurrent operations without locking, check for version conflicts on commit (uses version/timestamp columns). Good for low conflict.
*   **Concurrency Control Protocols (CCP)**
    *   Two-Phase Locking (2PL), Strict 2PL, Rigorous 2PL.
    *   Thomas' Write Rule.
    *   **Multi-Version Concurrency Control (MVCC):** Maintaining multiple physical versions of rows so reads don't block writes, and writes don't block reads (e.g., in PostgreSQL and MySQL InnoDB).
*   **Deadlocks**
    *   Detection (Wait-For Graph), Prevention (Wait-Die, Wound-Wait), and Recovery.

---

## 8. Transactions in Real Applications
*   **Lifecycle Commands**
    *   `BEGIN TRANSACTION` / `START TRANSACTION`.
    *   `COMMIT` (persists changes).
    *   `ROLLBACK` (discards changes).
    *   `SAVEPOINT` (partial rollbacks).
*   **Atomic Operations & Transaction Boundaries**
    *   Determining where a transaction should start and end in application code (Middleware, ORM `@Transactional` decorators).
*   **Long-Running Transactions (Anti-Patterns)**
    *   Why long transactions are bad:
        *   Locks are held too long, leading to concurrency blockages.
        *   Database connection pool starvation.
        *   Transaction log/undo segment bloat (MVCC row version cleanup gets delayed).
        *   Increased risk of deadlocks.
    *   *Best Practice:* Keep transactions small, quick, and focused. Avoid placing external network calls (e.g., calling a payment gateway) inside a database transaction block.

---

## 9. Storage, File Structures, Indexing & Query Optimization
*   **Storage & Buffer Pools**
    *   Buffer Pools, Buffer replacement policies (LRU), Dirty pages.
    *   RAID Levels (RAID 0, 1, 5, 10).
*   **Indexing Mechanics**
    *   Dense vs. Sparse Indexes.
    *   Clustered vs. Non-Clustered Indexes.
    *   B-Tree and B+ Tree structures (Node fan-out, Range scanning efficiency).
*   **Practical Indexing**
    *   **When/why indexes are used:** Speeds up data retrieval for specific search filters and sorts.
    *   **Composite Indexes:** Multi-column indexes.
    *   **Leftmost-Prefix Rule:** A composite index on `(A, B, C)` can speed up queries filtering by `(A)`, `(A, B)`, or `(A, B, C)`, but NOT queries filtering only by `(B)` or `(C)`.
    *   **Covering Indexes:** Indexes that contain all columns requested in the `SELECT` clause, allowing the database to return results directly from the index without reading the actual table data pages (Index-Only Scan).
    *   **Index Selectivity & Cardinality:** 
        *   *Cardinality:* Count of unique values in a column.
        *   *Selectivity:* Proportion of unique values (Cardinality / Total rows). High selectivity columns (e.g., User IDs) are great for indexes; low selectivity columns (e.g., Gender) are poor.
    *   **When an index is NOT useful:** Small tables, columns with low selectivity, columns undergoing heavy write/update volume (index maintenance overhead).
*   **Query Optimization & Analysis**
    *   **EXPLAIN / Execution Plans:** Inspecting how the database plans to run the query.
    *   **Access Paths:**
        *   *Table Scan / Sequential Scan:* Reading the entire table from disk.
        *   *Index Scan:* Reading the entire index structure.
        *   *Index Seek:* Directly traversing the B+ Tree to find matching rows.
    *   **Join Strategies (High Level):**
        *   *Nested Loop Join:* Good for small datasets.
        *   *Hash Join:* Builds in-memory hash table of one relation, probes with the other. Best for large, unsorted datasets.
        *   *Sort-Merge Join:* Sorts both tables on join key and merges them. Best if data is already sorted.
    *   **Common Causes of Slow Queries:** Missing indexes, N+1 queries, wildcards at the start of strings (e.g., `LIKE '%abc'`), sorting large unindexed columns, and suboptimal join structures.

---

## 10. Database Recovery Systems
*   **Log-Based Recovery**
    *   Write-Ahead Logging (WAL) protocol.
    *   Undo and Redo operations.
    *   Deferred vs. Immediate Modification techniques.
*   **Checkpoints**
    *   How checkpointing reduces recovery time.
*   **Shadow Paging**

---

## 11. Caching with Databases
*   **Why Caching is Needed**
    *   Alleviation of read load from primary databases.
    *   Lowering query latency (Memory access is nanoseconds vs. Milliseconds for disk).
*   **Caching Patterns**
    *   **Cache-Aside (Lazy Loading):** Application queries cache first. If a miss, reads DB, updates cache, and returns. (Highly popular).
    *   **Write-Through:** Application writes to cache, cache synchronously writes to DB. Ensures consistency.
    *   **Write-Behind / Write-Back:** Application writes to cache, cache asynchronously updates DB at intervals. High speed, risk of data loss.
*   **Cache Invalidation Strategies**
    *   TTL (Time-To-Live expiration).
    *   Write-invalidation (manual deletion/eviction on database write).
*   **Redis as a database cache** (Redis structures: Strings, Hashes, Sorted Sets).

---

## 12. Connection Pooling
*   **Why Connection Pools Exist**
    *   Opening a database connection requires a TCP handshake, TLS negotiation, and database backend process spawning.
    *   Creating a new connection per request incurs massive latency and CPU overhead.
*   **Mechanism**
    *   A warm pool of active connections is maintained.
    *   Application threads checkout a connection, execute queries, and return it to the pool immediately.
*   **Pool Size Tuning**
    *   Too small: Requests block waiting for connections.
    *   Too large: Exhausts database backend resources (max connection limits, OS thread context switching overhead).

---

## 13. Modern Databases & Scaling (System Design Concepts)
*   **SQL vs. NoSQL**
    *   Relational vs. Non-relational paradigms.
*   **Replication**
    *   **Primary-Replica (Leader-Follower) Architecture:** Writes go to primary, reads scaled to replicas.
    *   **Synchronous vs. Asynchronous Replication:**
        *   *Synchronous:* Primary waits for replica confirmation before acknowledging write. Strong consistency, high latency, write blockages if replica dies.
        *   *Asynchronous:* Primary writes locally and returns immediately. Replica updates later. Zero write latency penalty, risk of replica lag and data loss on primary crash.
    *   **Replication Lag:** The time delay between write on primary and its replication. Can lead to "Read-Your-Own-Writes" inconsistency.
    *   **Failover:** Promoting a replica to primary if primary fails.
*   **CAP & PACELC Theorems**
*   **Scaling & Sharding**
    *   Vertical vs. Horizontal scaling.
    *   **Sharding (Horizontal Partitioning):** Dividing data across multiple physical database servers based on a shard key. Range, Hash, and Directory sharding patterns.
