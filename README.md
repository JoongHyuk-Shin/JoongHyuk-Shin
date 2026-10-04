# JoongHyuk Shin
**Database Engine Developer | PostgreSQL contributor**

Seoul, South Korea | sjh910805@gmail.com | [GitHub](https://github.com/JoongHyuk-Shin) | [LinkedIn](https://www.linkedin.com/in/joonghyuk-shin)

---

### 🚀 Summary
- PostgreSQL contributor: authored a recovery-target fix committed to master for PostgreSQL 20; submitted two further patches on hot-standby buffer-pin waits and WAL recovery boundaries.
- Developed SQL compiler modules and PostgreSQL C extensions, including Oracle-compatible row-level security.
- Built lifecycle automation for Patroni/etcd PostgreSQL clusters on Azure: scale-out with rollback, scale-in, and a two-way transition between a single node and an HA cluster.

---

### 🛠 Skills
| Area | Details |
|------|--------|
| **Languages** | C, C++, Python, SQL, Java, Bash |
| **DB Internals** | SQL compilation, query rewriting, cost-based optimization, plan caching, WAL/PITR, physical replication, vector search |
| **PostgreSQL** | C extensions, planner hook, object access hook, RLS, parser/planner integration |
| **Distributed** | High availability (Patroni, etcd), cluster orchestration (IaC) |
| **Tools** | Linux, Docker, Git, Azure SDK and ARM templates |

---

### 💼 Work Experience

#### **Tmax Tibero** | Database Engine Developer (Oct 2023 - Present)

**1) OpenSQL Team (Nov 2024 - Present)**

PostgreSQL-based RDBMS with Oracle compatibility and vector DB features.

- **Row-Level Security (DBMS_RLS)**  
  Designed and implemented Oracle-compatible DBMS_RLS in a **PostgreSQL C extension**, using **planner_hook** for transient-view predicate injection and definer-rights policy functions. Added policy checks for rows written by INSERT/UPDATE when write validation is enabled, and automatic policy cleanup on table drops through **object_access_hook**.
  Added recursive policy application within predicate subqueries and column-sensitive policy activation through `sec_relevant_cols`.

- **Oracle compatibility**  
  Implemented and extended Oracle-compatible functions and packages (NVL/NVL2, EXISTSNODE, DUMP, DBMS_RANDOM, DBMS_ALERT).
  Replaced the full sort in the median aggregate with quickselect, improving performance by up to 60% in a 10M-row test.

- **C extension debugging**  
  Fixed an NVL-extension segmentation fault caused by returning inside `PG_TRY` before `PG_END_TRY` restored exception state; added a regression test that triggers an error in a subsequent query.

- **Query-tree debugging**  
  Built internal debug tooling to print PostgreSQL query trees during development.

- **Cluster orchestration & scaling**  
  Designed and built a Python cluster-scaling tool invoked by the control plane and operators, with a cloud-provider interface and Azure ARM provisioning: it adds and removes Patroni nodes, polls etcd until the new member is running, and rolls back a failed scale-out with an idempotent VM delete.
  Integrated lifecycle progress and result reporting with the control plane, including bounded retries for transient reporting failures.
  Added a cumulative stall-time limit to Patroni join monitoring, allowing progressing replication to continue while failed joins trigger rollback.

- **High availability**  
  Designed PostgreSQL HA environments using Patroni and etcd for enterprise workloads.
  Automated two-way Azure transitions between a single PostgreSQL node and a Patroni HA cluster with two data nodes and an etcd witness, including learner promotion and VIP configuration/removal.
  Implemented failed-expansion rollback that removes added etcd members before deleting the new data-node VM, configured proxy VIP failover to the new leader, and added real-cluster end-to-end tests for both directions.

- **Connection routing**  
  Extended a pgcat-based Rust proxy to route `BEGIN READ ONLY` transactions to replicas when the pool disables primary reads; added a unit test covering read-only and read/write transaction routing.
  In a fixed-rate pgJDBC benchmark, shifted all tested recursive-CTE reads from primary to replica while UPDATEs stayed on primary.

- **Performance diagnosis**  
  Investigated a report of higher PostgreSQL backend CPU through the proxy using a throughput-matched experiment; reproduced pgJDBC-induced primary routing skew and measured comparable backend CPU for direct and proxied connections.

- **Vector search (schema linking)**  
  Built a schema-linking API using FastAPI, pgvector and Ollama to embed JSON schema metadata and retrieve relevant tables through cosine-similarity search; packaged it with Docker Compose.

**2) SuperTibero Team (Oct 2023 - Oct 2024)**

Proprietary RDBMS with distributed storage; worked on SQL compiler modules.

- **SQL compiler**  
  Developed modules of the parser, query transformer, and cost-based optimizer.
  Reduced AST child traversal from two passes to one and outer-join relationship setup from O(n) to O(1).

- **Query optimization**  
  Designed and implemented predicate pull-up and push-down across 22 logical-plan node types, with join-type-aware branch selection, and IN-subquery-to-EXISTS conversion.
  Designed and implemented predicate derivation for non-equi joins and compound expressions, and predicate distribution into set-operation query blocks.
  Designed and implemented null-aware self-comparison rewrites and elimination of redundant or contradictory predicates.
  Fixed index range scan cardinality estimation that had forced index full scans for `<` predicates, repaired sort elimination, and improved plan cache matching.
  Fixed query-block expression-ID allocation and plan-cache invalidation for dropped sequences.

- **Privilege check**  
  Designed and implemented the privilege check at hard parse for SELECT, INSERT, UPDATE, DELETE, and MERGE, caching permissions per level to cut repeated checks.

---

### Open Source
- **PostgreSQL**  
  - Authored a recovery-target fix committed to PostgreSQL master for PostgreSQL 20 ([d5751c33cc3](https://git.postgresql.org/cgit/postgresql.git/commit/?id=d5751c33cc3)): prevented GUC assignment order from clearing a configured recovery target, moved cross-parameter validation out of assign hooks, and added recovery tests.
  - Credited as reviewer on a committed PostgreSQL test-framework change that preserved postmaster cleanup when tests supplied startup options ([1009339b3ac](https://git.postgresql.org/cgit/postgresql.git/commit/?id=1009339b3ac)).
  - Submitted "Prevent repeated deadlock-check signals in standby buffer pin waits" to pgsql-hackers and the November 2026 CommitFest.
  - Submitted "Add recovery boundary WAL record for database and tablespace commands" to pgsql-hackers and the November 2026 CommitFest.

- **TimescaleDB**  
  - Fixed an assertion failure in `add_dimension()` when the hypertable argument is NULL; it now raises an error instead ([#10327](https://github.com/timescale/timescaledb/pull/10327), released in 2.29.1 and 2.30.0).

---

### Technical Writing
- Published Chapter 1 (Query Processing; 25 sections) of a PostgreSQL internals series in English ([dev.to](https://dev.to/joonghyukshin)) and Korean ([velog](https://velog.io/@sjh910805/series)); Chapter 2 (Storage & Access Methods) in progress.

---

### 🎓 Education
- **B.S. in Physics**, Yonsei University, Seoul
  - Focus: **Statistical Mechanics**, Quantum Mechanics

---

### 🏆 Achievements & Certifications
- **Algorithms**
  - [LeetCode](https://leetcode.com/Joshua-Shin/): 100 Days Badge in 2023 and 2024.
    <br><br> ![LeetCode Badges](https://leetcode-badge-showcase.vercel.app/api?username=Joshua-Shin)
  - **Top 3.5%** on [Baekjoon](https://solved.ac/profile/sjh910805) - Platinum V
    
     <img src="http://mazassumnida.wtf/api/v2/generate_badge?boj=sjh910805">

- **Certifications**
  - Engineer Information Processing (HRDK)
  - SQL Developer (SQLD, Kdata)
