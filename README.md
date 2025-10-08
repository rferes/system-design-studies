# 🏗️ System Design Studies

> Fundamentos de arquitetura escalável, padrões de design e preparação para entrevistas de system design

[![System Design](https://img.shields.io/badge/System-Design-blue.svg)]()
[![Architecture](https://img.shields.io/badge/Architecture-Patterns-green.svg)]()

---

## 📚 Estrutura do Repositório

```
.
├── fundamentals/              # Conceitos base
│   ├── scalability/
│   │   ├── load-balancing.md
│   │   ├── caching.md
│   │   ├── database-scaling.md
│   │   └── cdn.md
│   ├── databases/
│   │   ├── sql-vs-nosql.md
│   │   ├── sharding.md
│   │   ├── replication.md
│   │   └── cap-theorem.md
│   ├── caching/
│   │   ├── cache-strategies.md
│   │   ├── redis-patterns.md
│   │   └── cdn.md
│   └── networking/
│       ├── protocols.md
│       ├── dns.md
│       └── api-design.md
├── system-designs/            # Sistemas completos
│   ├── url-shortener/
│   ├── instagram/
│   ├── twitter-feed/
│   ├── uber/
│   ├── youtube/
│   └── whatsapp/
├── patterns/                  # Padrões arquiteturais
│   ├── microservices.md
│   ├── event-driven.md
│   ├── cqrs.md
│   └── saga-pattern.md
├── diagrams/                  # Diagramas visuais
└── docs/                      # Templates e guias
```

---

## 🎯 Roadmap de Estudo

### Semana 7: Fundamentos (18-22/11)

#### Dia 1 (18/11) - Scalability Basics
- [ ] Load Balancing (Round-robin, Least connections, Consistent hashing)
- [ ] Horizontal vs Vertical scaling
- [ ] Stateless vs Stateful services
- [ ] CDN (Content Delivery Network)
- [ ] 📝 **25 flashcards**
- [ ] Desenhar 3 arquiteturas escaláveis

#### Dia 2 (19/11) - Caching Strategies
- [ ] Cache-aside (Lazy loading)
- [ ] Write-through
- [ ] Write-behind (Write-back)
- [ ] Cache invalidation
- [ ] Cache eviction policies (LRU, LFU)
- [ ] Redis patterns
- [ ] 📝 **20 flashcards**

#### Dia 3 (20/11) - Database Scaling
- [ ] Sharding strategies (Range, Hash, Directory)
- [ ] Replication (Master-Slave, Multi-master)
- [ ] Partitioning
- [ ] Database indexing
- [ ] ACID vs BASE
- [ ] 📝 **25 flashcards**

#### Dia 4 (21/11) - Message Queues & Async
- [ ] Message queues (RabbitMQ, Kafka, SQS)
- [ ] Pub/Sub pattern
- [ ] Event-driven architecture
- [ ] Async processing
- [ ] Dead letter queues
- [ ] 📝 **20 flashcards**

#### Dia 5 (22/11) - APIs & Microservices
- [ ] REST best practices
- [ ] GraphQL
- [ ] gRPC
- [ ] API Gateway pattern
- [ ] Service discovery
- [ ] Circuit breaker
- [ ] 📝 **25 flashcards**

### Semana 8-9: Prática de System Design

#### Mock Interviews (29/11)
- [ ] Design URL Shortener (30min)
- [ ] Design Twitter Feed (30min)
- [ ] Design Instagram (45min)

---

## 📖 Fundamentos por Categoria

### 🔄 Scalability

| Tópico | Descrição | Status |
|--------|-----------|--------|
| Load Balancing | Distribuir tráfego entre servidores | 🔴 |
| Caching | CDN, Redis, Application cache | 🔴 |
| Database Scaling | Sharding, replication, partitioning | 🔴 |
| Message Queues | Kafka, RabbitMQ, async processing | 🔴 |
| Microservices | Service decomposition, communication | 🔴 |

### 💾 Databases

| Tópico | Descrição | Status |
|--------|-----------|--------|
| SQL vs NoSQL | Quando usar cada um | 🔴 |
| Sharding | Estratégias de sharding | 🔴 |
| Replication | Master-slave, multi-master | 🔴 |
| CAP Theorem | Consistency, Availability, Partition tolerance | 🔴 |
| Transactions | ACID, isolation levels | 🔴 |

### 🎯 Caching

| Tópico | Descrição | Status |
|--------|-----------|--------|
| Cache Strategies | Cache-aside, write-through, write-behind | 🔴 |
| CDN | Content delivery network | 🔴 |
| Redis Patterns | Common use cases | 🔴 |
| Cache Invalidation | Estratégias de invalidação | 🔴 |

### 🌐 Networking & APIs

| Tópico | Descrição | Status |
|--------|-----------|--------|
| HTTP/HTTPS | Protocols, methods, status codes | 🔴 |
| REST | RESTful API design | 🔴 |
| GraphQL | Query language for APIs | 🔴 |
| WebSockets | Real-time communication | 🔴 |
| gRPC | High performance RPC framework | 🔴 |

---

## 🎨 System Designs Completos

### 1. URL Shortener (Básico)

**Complexidade:** ⭐ Fácil  
**Tempo:** 30-45 minutos  
**Status:** 🔴 Pendente

**Requisitos:**
- Encurtar URLs longas
- Redirecionar para URL original
- Analytics (clicks, geo)
- Custom short URLs

**Conceitos cobertos:**
- Hashing
- Database design
- Caching
- Rate limiting

[Ver design completo](./system-designs/url-shortener/)

---

### 2. Twitter Feed (Intermediário)

**Complexidade:** ⭐⭐ Médio  
**Tempo:** 45-60 minutos  
**Status:** 🔴 Pendente

**Requisitos:**
- Post tweets
- Follow/unfollow users
- Timeline feed (home & user)
- Notifications
- Trending topics

**Conceitos cobertos:**
- Fan-out pattern
- Timeline generation
- Caching strategies
- Message queues

[Ver design completo](./system-designs/twitter-feed/)

---

### 3. Instagram (Complexo)

**Complexidade:** ⭐⭐⭐ Difícil  
**Tempo:** 60+ minutos  
**Status:** 🔴 Pendente

**Requisitos:**
- Upload/download photos
- Follow users
- Photo feed
- Like, comment
- Stories (24h expiration)

**Conceitos cobertos:**
- Object storage (S3)
- CDN
- Image processing
- Database sharding
- Caching layers

[Ver design completo](./system-designs/instagram/)

---

### 4. Uber (Complexo)

**Complexidade:** ⭐⭐⭐ Difícil  
**Tempo:** 60+ minutos  
**Status:** 🔴 Pendente

**Requisitos:**
- Rider requests ride
- Driver matching
- Real-time location tracking
- Pricing (surge)
- Trip history

**Conceitos cobertos:**
- Geospatial indexing (QuadTree, Geohash)
- WebSockets for real-time
- Dynamic pricing
- Notification system

[Ver design completo](./system-designs/uber/)

---

### 5. YouTube (Muito Complexo)

**Complexidade:** ⭐⭐⭐⭐ Muito Difícil  
**Tempo:** 60+ minutos  
**Status:** 🔴 Pendente

**Requisitos:**
- Upload videos
- Stream videos
- Search videos
- Recommendations
- Comments, likes

**Conceitos cobertos:**
- Video processing pipeline
- Adaptive bitrate streaming
- CDN
- Recommendation engine
- Search indexing

[Ver design completo](./system-designs/youtube/)

---

### 6. WhatsApp (Muito Complexo)

**Complexidade:** ⭐⭐⭐⭐ Muito Difícil  
**Tempo:** 60+ minutos  
**Status:** 🔴 Pendente

**Requisitos:**
- Send/receive messages (1-to-1, group)
- Message delivery confirmation
- Online/offline status
- Media sharing
- End-to-end encryption

**Conceitos cobertos:**
- WebSockets
- Message queues
- Delivery acknowledgments
- Group chat scaling
- Encryption

[Ver design completo](./system-designs/whatsapp/)

---

## 📊 Framework de System Design Interview

### Passo 1: Requirements (5 min)

**Perguntas a fazer:**
- Quais features são mais importantes?
- Quantos usuários? (DAU, MAU)
- Read-heavy ou write-heavy?
- Consistência vs Disponibilidade?
- Latência esperada?

### Passo 2: Estimativas (5 min)

**Calcular:**
- Traffic estimates (QPS)
- Storage estimates
- Bandwidth estimates
- Memory estimates (cache)

### Passo 3: High-Level Design (15 min)

**Desenhar:**
- Client → Load Balancer → Servers
- Database layer
- Cache layer
- CDN (se aplicável)

### Passo 4: Deep Dives (20 min)

**Detalhar:**
- Database schema
- API design
- Algoritmos críticos
- Bottlenecks e soluções

### Passo 5: Wrap-up (5 min)

**Discutir:**
- Monitoring & alerting
- Deployment strategy
- Testing strategy
- Future improvements

---

## 🎓 Patterns Arquiteturais

### Microservices

**Quando usar:**
- Sistema grande e complexo
- Equipes independentes
- Deploy independente necessário

**Trade-offs:**
- ✅ Escalabilidade independente
- ✅ Tecnologias diferentes
- ❌ Complexidade operacional
- ❌ Latência de rede

### Event-Driven

**Quando usar:**
- Async processing
- Desacoplamento de serviços
- Real-time updates

**Trade-offs:**
- ✅ Desacoplamento
- ✅ Escalabilidade
- ❌ Debugging complexo
- ❌ Eventual consistency

### CQRS (Command Query Responsibility Segregation)

**Quando usar:**
- Read e write patterns diferentes
- Performance crítica
- Auditing necessário

**Trade-offs:**
- ✅ Otimização independente
- ✅ Escalabilidade
- ❌ Complexidade
- ❌ Eventual consistency

---

## 📊 Progresso Geral

```
Fundamentos Estudados: 0/20 (0%)
System Designs Completos: 0/6 (0%)
Mock Interviews: 0/3 (0%)
Flashcards: 0/115 (0%)
Diagramas Desenhados: 0/10 (0%)
```

**Meta:** Dominar 6 system designs até fim da Semana 9

---

## 💡 Números para Memorizar

### Latências
- L1 cache: ~1 ns
- L2 cache: ~4 ns
- RAM: ~100 ns
- SSD: ~16 μs
- HDD: ~2 ms
- Network (same datacenter): ~500 μs
- Network (cross-continental): ~150 ms

### Throughput
- RAM: ~10 GB/s
- SSD: ~500 MB/s
- HDD: ~100 MB/s
- 1 Gbps network: ~125 MB/s

### Capacidades
- Character: 1 byte
- Integer: 4 bytes
- Unix timestamp: 4 bytes
- Tweet: 280 chars = ~280 bytes
- Image (compressed): ~200 KB
- Video minute (720p): ~50 MB

---

## 🚀 Como Usar Este Repositório

### Estudar um Fundamento

```bash
# Ler tópico
cat fundamentals/scalability/load-balancing.md

# Desenhar diagrama
# Usar papel ou ferramenta online
```

### Praticar um System Design

1. Ler requisitos em `system-designs/[sistema]/`
2. Tentar resolver sozinho (45-60min)
3. Comparar com solução documentada
4. Identificar gaps no conhecimento

### Preparar para Mock Interview

1. Escolher sistema aleatório
2. Timer de 45 minutos
3. Desenhar solução no papel
4. Gravar explicação
5. Revisar gravação

---

## 📖 Recursos Recomendados

### Livros
- [Designing Data-Intensive Applications](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/) - Martin Kleppmann
- [System Design Interview](https://www.amazon.com/System-Design-Interview-insiders-Second/dp/B08CMF2CQF) - Alex Xu
- [Web Scalability for Startup Engineers](https://www.amazon.com/Scalability-Startup-Engineers-Artur-Ejsmont/dp/0071843655)

### Online
- [System Design Primer](https://github.com/donnemartin/system-design-primer) - GitHub
- [Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview)
- [ByteByteGo](https://bytebytego.com/)

### Vídeos
- [Gaurav Sen - System Design](https://www.youtube.com/c/GauravSensei)
- [Tech Dummies](https://www.youtube.com/c/TechDummiesNarendraL)
- [Success in Tech](https://www.youtube.com/c/SuccessinTech)

### Blogs
- [High Scalability](http://highscalability.com/)
- [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/)
- [Netflix Tech Blog](https://netflixtechblog.com/)
- [Uber Engineering Blog](https://eng.uber.com/)

---

## 🎴 Flashcards Template

Ver `docs/flashcards-template.md` para formato de flashcards de system design.

---

## 📝 Notas

Este repositório documenta o estudo de system design durante as Semanas 7-9 (18/11 - 06/12/2025). Foco em preparação para entrevistas de system design em posições senior backend.

---

## 📫 Contribuições

Sugestões de melhorias via [issues](https://github.com/seu-username/system-design-studies/issues)!

---

**Status:** 🚧 Início previsto para 18/11/2025  
**Meta:** 6 system designs dominados + 115 flashcards
