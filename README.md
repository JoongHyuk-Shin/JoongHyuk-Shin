# JoongHyuk Shin
**System-level Software Engineer specializing in Database Engine Kernels & Distributed Coordination**

---

### 🚀 Summary
- System-level software engineer specializing in database engine kernels and distributed coordination.
- Expertise in extending PostgreSQL with C extensions, hooks (planner, object access), Vector/LLM integration, and Oracle-compatible features.
- Experience architecting distributed lifecycle engines with a focus on transactional state consistency and reliability.
- Proficient in C, C++, Python, and Linux; solid foundation in algorithms, probability, and high-performance distributed system design.

---

### 🛠 Skills
| Area | Details |
|------|--------|
| **Languages** | C, C++ (Modern), Python, SQL, Java, Bash |
| **DB Internals** | PostgreSQL/Oracle engine core, query compiler, optimizer (CBO), vector search |
| **PostgreSQL** | C extensions, planner hook, object access hook, RLS, parser/planner integration |
| **Distributed** | Consensus (etcd/Raft), high availability, cluster orchestration (IaC) |
| **Core** | Probability, high-performance algorithms |
| **Tools** | Linux (system-level), Docker, Git, AWS/Azure (SDK/API integration) |

---

### 💼 Work Experience

#### **Tmax Tibero** | Database Engine Developer (Oct 2023 – Present)

**1) OpenSQL Team (Nov 2024 – Present)**

PostgreSQL-based managed RDBMS with Oracle compatibility and vector DB features.

- **Row-Level Security (DBMS_RLS)**  
  Designed and implemented Oracle-compatible RLS as a **PostgreSQL C extension**, using **planner_hook** and **object_access_hook** for planner integration and runtime policy enforcement. Delivered transient-view–style predicate injection and definer-rights policy execution aligned with Oracle VPD semantics.

- **Oracle compatibility**  
  Implemented Oracle-compatible functions/packages and conducted performance benchmarking; achieved measurable improvements including 50%+ gain for the median function through algorithm redesign.

- **Vector DB & RAG**
  Built and deployed a schema-linking API (FastAPI + pgvector): ingests DB schema definitions (DD JSON), generates vector embeddings via Ollama, and returns semantically relevant tables for natural language queries using cosine similarity search. Deployed as a Docker Compose service (pgvector + app).

- **High availability**  
  Designed PostgreSQL HA environments using Patroni and etcd for enterprise workloads.

- **Cluster orchestration & scaling**  
  Architected a Multi-CSP IaC (ARM/CloudFormation) scaling engine using etcd watch for real-time state sync and Command Pattern–based rollback for transactional reliability in distributed node lifecycle.

- **Debug / monitoring**  
  Built internal debug tooling to print PostgreSQL query trees during development.

**2) SuperTibero Team (Oct 2023 – Oct 2024)**

Enterprise RDBMS with distributed storage; focused on SQL compiler modules.

- **SQL compiler**  
  Built parser, query transformer, and cost-based optimizer.

- **Query optimization**  
  Implemented index range scan, predicate pushdown, sort-skip optimization, and execution plan cache.

- **Privilege & authentication**  
  Designed and implemented privilege check and authentication for secure SQL execution.

- **Performance**  
  Delivered query transformation features that improved index scan opportunities and reduced redundant operations.

---

### 🎓 Education
- **B.S. in Physics** – Yonsei University, Seoul
  - Focus: **Statistical Mechanics**, Quantum Mechanics

---

### 🏆 Achievements & Certifications
- **Algorithms**
  - **Top 4.2%** Contributor on [Leetcode](https://leetcode.com/Joshua-Shin/) (Consecutive years: 2023, 2024)
    <br><br> ![LeetCode Badges](https://leetcode-badge-showcase.vercel.app/api?username=Joshua-Shin)`
  - **Top 3.5%** on [Baekjoon](https://solved.ac/profile/sjh910805) - Platinum V
    
     <img src="http://mazassumnida.wtf/api/v2/generate_badge?boj=sjh910805">

- **Certifications**
  - Engineer Information Processing (HRDK)
  - SQL Developer (SQLD, Kdata)

---

### 📫 Connect with Me
- [GitHub](https://github.com/JoongHyuk-Shin)
- [LinkedIn](www.linkedin.com/in/joonghyuk-shin-631701201)
- sjh910805@gmail.com
