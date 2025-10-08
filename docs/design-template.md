# Design: [Nome do Sistema]

> 📅 Data: [DD/MM/2025]  
> ⏱️ Tempo de design: [X minutos]  
> 🎯 Complexidade: [⭐ Fácil | ⭐⭐ Médio | ⭐⭐⭐ Difícil]

---

## 1️⃣ Requirements Clarification (5 min)

### Functional Requirements

**Prioridade Alta:**
- [ ] FR1: [Descrição]
- [ ] FR2: [Descrição]
- [ ] FR3: [Descrição]

**Prioridade Baixa (out of scope):**
- [ ] FR4: [Descrição]
- [ ] FR5: [Descrição]

### Non-Functional Requirements

- [ ] **Scalability:** Suportar X usuários simultâneos
- [ ] **Availability:** 99.9% uptime
- [ ] **Latency:** < Xms para operação Y
- [ ] **Consistency:** [Strong | Eventual]
- [ ] **Durability:** Dados não podem ser perdidos

### Extended Requirements (Nice to have)

- [ ] Analytics e metrics
- [ ] Monitoring
- [ ] Rate limiting

---

## 2️⃣ Capacity Estimation (5 min)

### Traffic Estimates

**Assumptions:**
- Total users: [X million]
- Daily Active Users (DAU): [Y million]
- Average requests per user per day: [Z]

**Calculations:**
```
QPS (Queries Per Second):
= (DAU × requests/day) / 86400 seconds
= [resultado]

Peak QPS (3x average):
= [resultado × 3]
```

### Storage Estimates

**Per item storage:**
- Metadata: [X KB]
- Media (if applicable): [Y MB]

**Total storage:**
```
Daily new items: [N]
Storage per day: N × size
Storage per year: daily × 365
With replication (3x): yearly × 3
```

### Bandwidth Estimates

```
Incoming data: [X GB/s]
Outgoing data: [Y GB/s]
```

### Memory (Cache) Estimates

**80/20 rule:** 80% of traffic from 20% of content

```
Cache size = 20% of daily data
= [resultado]
```

---

## 3️⃣ System APIs (10 min)

### API 1: [Nome da operação]

**Endpoint:** `POST /api/v1/[resource]`

**Request:**
```json
{
  "field1": "value",
  "field2": "value"
}
```

**Response:**
```json
{
  "id": "uuid",
  "status": "success",
  "data": {}
}
```

**Status Codes:**
- 200: Success
- 400: Bad request
- 401: Unauthorized
- 429: Rate limit exceeded
- 500: Internal error

### API 2: [Nome]

[Repetir estrutura]

---

## 4️⃣ High-Level Design (15 min)

### Architecture Diagram

```
┌─────────┐
│  Client │
└────┬────┘
     │
     ▼
┌─────────────────┐
│  Load Balancer  │
└────┬────────────┘
     │
     ▼
┌─────────────────────────────────┐
│   Application Servers (N)       │
│  ┌──────┐ ┌──────┐ ┌──────┐    │
│  │ API  │ │ API  │ │ API  │    │
│  └──────┘ └──────┘ └──────┘    │
└──┬───────────────────────────┬──┘
   │                           │
   ▼                           ▼
┌─────────┐              ┌──────────┐
│  Cache  │              │ Database │
│ (Redis) │              │  (SQL)   │
└─────────┘              └──────────┘
```

### Components

#### Load Balancer
- **Purpose:** Distribute traffic
- **Algorithm:** Round-robin / Least connections
- **Health checks:** Yes

#### Application Servers
- **Purpose:** Business logic
- **Language:** Python (FastAPI/Django)
- **Stateless:** Yes
- **Auto-scaling:** Based on CPU/memory

#### Cache Layer
- **Technology:** Redis
- **Purpose:** Reduce database load
- **Strategy:** Cache-aside
- **TTL:** [X hours/days]
- **Eviction:** LRU

#### Database
- **Type:** [SQL/NoSQL]
- **Technology:** PostgreSQL / MongoDB
- **Purpose:** Persistent storage
- **Replication:** Master-Slave
- **Sharding:** [Yes/No, strategy]

#### CDN (if applicable)
- **Purpose:** Serve static content
- **Coverage:** Global

#### Message Queue (if applicable)
- **Technology:** Kafka / RabbitMQ
- **Purpose:** Async processing
- **Use cases:** [Lista]

---

## 5️⃣ Database Design (10 min)

### Schema (SQL Example)

```sql
-- Users table
CREATE TABLE users (
    id UUID PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT NOW(),
    INDEX idx_username (username),
    INDEX idx_email (email)
);

-- [Outras tabelas]
CREATE TABLE [table_name] (
    id UUID PRIMARY KEY,
    user_id UUID REFERENCES users(id),
    -- outros campos
    created_at TIMESTAMP DEFAULT NOW()
);
```

### Indexes

| Table | Column | Type | Reason |
|-------|--------|------|--------|
| users | username | B-tree | Fast lookup |
| users | email | B-tree | Fast lookup |
| posts | created_at | B-tree | Sorting |

### Sharding Strategy (if applicable)

**Shard key:** [Campo usado para sharding]  
**Reason:** [Justificativa]  
**Number of shards:** [N]

**Example:**
- Shard 1: user_id % 10 = 0
- Shard 2: user_id % 10 = 1
- ...

---

## 6️⃣ Deep Dives (20 min)

### Deep Dive 1: [Componente/Feature crítico]

**Problem:** [Descrever o desafio]

**Solution:**

**Approach 1:**
- Description
- ✅ Pros: [Lista]
- ❌ Cons: [Lista]

**Approach 2:**
- Description
- ✅ Pros: [Lista]
- ❌ Cons: [Lista]

**Chosen Solution:** Approach [X]  
**Reason:** [Justificativa]

**Implementation Details:**
```
[Pseudo-code ou descrição técnica]
```

### Deep Dive 2: [Outro componente]

[Repetir estrutura]

---

## 7️⃣ Bottlenecks & Solutions (5 min)

### Bottleneck 1: Database becomes read bottleneck

**Problem:** Too many reads  
**Solution:** 
- Add Redis cache layer
- Read replicas
- Cache-aside pattern

### Bottleneck 2: Single point of failure

**Problem:** Load balancer fails  
**Solution:**
- Multiple load balancers
- Health checks
- Failover mechanism

### Bottleneck 3: [Outro]

[Continuar...]

---

## 8️⃣ Monitoring & Observability

### Metrics to Track

**Application:**
- Request rate (QPS)
- Response time (p50, p95, p99)
- Error rate
- Success rate

**Infrastructure:**
- CPU utilization
- Memory usage
- Disk I/O
- Network bandwidth

**Business:**
- Active users
- Conversion rate
- [KPIs específicos]

### Alerts

- Response time > 500ms
- Error rate > 1%
- CPU > 80%
- Database connections > 80%

### Logging

- Structured logging (JSON)
- Log levels: DEBUG, INFO, WARN, ERROR
- Centralized logging (ELK, CloudWatch)

---

## 9️⃣ Security Considerations

- [ ] HTTPS everywhere
- [ ] Authentication (JWT, OAuth)
- [ ] Authorization (RBAC)
- [ ] Rate limiting (per user, per IP)
- [ ] Input validation
- [ ] SQL injection prevention
- [ ] XSS prevention
- [ ] CSRF tokens
- [ ] Data encryption at rest
- [ ] PII data handling

---

## 🔟 Extended Features (Future)

### Phase 2
- [ ] Feature A
- [ ] Feature B

### Phase 3
- [ ] Feature C
- [ ] Feature D

---

## 📊 Trade-offs Made

### Trade-off 1: Eventual Consistency

**Decision:** Use eventual consistency for [feature]  
**Reason:** Better availability and performance  
**Impact:** Users may see stale data for [X seconds]  
**Acceptable:** Yes, because [justificativa]

### Trade-off 2: [Outro]

[Repetir...]

---

## 🎓 Key Learnings

### What went well
- [Aprendizado 1]
- [Aprendizado 2]

### What could be improved
- [Ponto 1]
- [Ponto 2]

### Patterns used
- [Pattern 1]
- [Pattern 2]

---

## 🔗 References

- [Link para sistema similar]
- [Artigo relevante]
- [Tech blog post]

---

## ✅ Interview Checklist

- [ ] Clarified requirements (functional + non-functional)
- [ ] Did capacity estimation
- [ ] Drew high-level design
- [ ] Defined APIs
- [ ] Designed database schema
- [ ] Identified bottlenecks
- [ ] Proposed solutions
- [ ] Discussed monitoring
- [ ] Considered security
- [ ] Asked clarifying questions
- [ ] Thought out loud

---

**Status:** [🔴 Draft | 🟡 In Progress | 🟢 Complete]  
**Review Date:** [DD/MM/2025]  
**Time Spent:** [X minutes]
