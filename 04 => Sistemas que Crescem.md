# Sistemas que Crescem

## Escalabilidade, Arquitetura, Performance e System Design

> **Objetivo:** entender como pensar, projetar e evoluir sistemas que precisam lidar com **mais usuários, mais requisições, mais dados e mais complexidade**.

- Material organizado com auxílio do **ChatGPT (GPT-5.6 Luna)**
  
---

# 1. O problema

Um sistema pode começar simples:

```text
Usuário
   ↓
Backend
   ↓
Banco de dados
```

Conforme cresce, começam a surgir problemas:

* Mais usuários simultâneos
* Mais requisições
* Mais dados
* Maior latência
* Gargalos
* Falhas
* Maior custo
* Necessidade de disponibilidade
* Mais serviços e dependências

A área que estuda como lidar com isso envolve principalmente:

> **Arquitetura de Software + System Design + Sistemas Distribuídos + Performance + Escalabilidade**

---

# 2. Escalabilidade

### O que é?

É a capacidade de um sistema **crescer sem perder desempenho ou disponibilidade de forma inaceitável**.

### Estudar

* Escalabilidade vertical
* Escalabilidade horizontal
* Load balancing
* Replicação
* Auto scaling
* Stateless applications
* Bottlenecks
* Throughput
* Latência

### Buscar

```text
"horizontal vs vertical scaling"
"load balancing explained"
"stateless application"
"system scalability"
"system bottlenecks"
```

---

# 3. Performance

### O que é?

Estuda **quão rápido e eficientemente** o sistema executa suas tarefas.

Uma pergunta importante:

> "Por que meu sistema está lento?"

### Estudar

* Latência
* Throughput
* CPU
* Memória
* I/O
* Network
* Profiling
* Benchmark
* Otimização
* Performance de queries

### Buscar

```text
"backend performance optimization"
"latency vs throughput"
"application profiling"
"database query optimization"
```

---

# 4. Bancos de Dados

Uma das áreas mais importantes para sistemas que crescem.

### Estudar

* Índices
* Query optimization
* Normalização
* Denormalização
* Transactions
* Isolation
* Connection pooling
* Replicação
* Read replicas
* Partitioning
* Sharding
* SQL vs NoSQL

### Pergunta importante

> "Como armazenar e consultar milhões/bilhões de registros sem destruir a performance?"

### Buscar

```text
"database indexing"
"database replication"
"database partitioning"
"database sharding"
"SQL query optimization"
"SQL vs NoSQL"
```

---

# 5. Cache

### O que é?

Guardar temporariamente informações que são acessadas com frequência para evitar trabalho desnecessário.

```text
Usuário
   ↓
Backend
   ↓
Cache ──→ encontrou → resposta
   │
   └──→ não encontrou
            ↓
          Banco
```

### Estudar

* Cache-aside
* TTL
* Cache invalidation
* Cache hit / miss
* Distributed cache
* Redis
* Memcached

### Buscar

```text
"caching strategies"
"cache aside pattern"
"Redis caching"
"cache invalidation"
```

---

# 6. Filas e processamento assíncrono

### O que é?

Permite tirar trabalhos demorados do caminho principal da requisição.

```text
API
 ↓
Fila
 ↓
Worker
 ↓
Processamento
```

Em vez de fazer tudo durante a requisição, algumas tarefas podem ser processadas depois.

### Estudar

* Message Queue
* Producer
* Consumer
* Worker
* Retry
* Dead Letter Queue
* Event-driven architecture
* Kafka
* RabbitMQ
* Amazon SQS

### Buscar

```text
"message queues explained"
"asynchronous processing"
"event driven architecture"
"Kafka basics"
"RabbitMQ basics"
```

---

# 7. Sistemas Distribuídos

### O que é?

Estuda sistemas compostos por **várias máquinas/processos que precisam trabalhar juntos**.

```text
Servidor A ←→ Servidor B
     ↕             ↕
Servidor C ←→ Banco
```

Quando existe distribuição, surgem problemas que não existem em um programa isolado.

### Estudar

* Replicação
* Consistência
* Disponibilidade
* Particionamento
* Fault tolerance
* Eventual consistency
* CAP theorem
* Consensus
* Distributed transactions
* Idempotência
* Comunicação entre serviços

### Buscar

```text
"distributed systems fundamentals"
"CAP theorem"
"eventual consistency"
"distributed systems failures"
"idempotency distributed systems"
```

---

# 8. Confiabilidade

### O que é?

É pensar em como o sistema continua funcionando **mesmo quando coisas dão errado**.

Perguntas:

> E se o banco cair?

> E se um servidor morrer?

> E se uma API externa ficar indisponível?

> E se uma requisição for processada duas vezes?

### Estudar

* Redundância
* Failover
* Retry
* Timeout
* Circuit Breaker
* Health Check
* Backup
* Disaster Recovery
* RTO
* RPO
* Idempotência

### Buscar

```text
"software reliability"
"fault tolerance"
"circuit breaker pattern"
"retry pattern"
"disaster recovery"
"RTO vs RPO"
```

---

# 9. Observabilidade

### O que é?

É conseguir **entender o que está acontecendo dentro de um sistema em produção**.

Os três pilares clássicos:

```text
┌──────────────┐
│ Observability│
├──────────────┤
│ Logs         │
│ Metrics      │
│ Traces       │
└──────────────┘
```

### Estudar

* Logs
* Métricas
* Distributed tracing
* Monitoring
* Alerting
* Dashboards
* OpenTelemetry
* Prometheus
* Grafana

### Buscar

```text
"observability fundamentals"
"logs metrics traces"
"distributed tracing"
"OpenTelemetry basics"
```

---

# 10. Arquitetura de Software

### O que é?

É estudar como **organizar as partes de um sistema**, suas responsabilidades e seus relacionamentos.

### Estudar

* Monólito
* Monólito modular
* Microservices
* Modularidade
* Coupling
* Cohesion
* Layered architecture
* Hexagonal architecture
* Clean Architecture
* Event-driven architecture
* Trade-offs arquiteturais

### Importante

Não decorar:

> "Sistema grande = microservices."

O objetivo é aprender:

> **"Qual arquitetura faz sentido para este problema?"**

### Buscar

```text
"software architecture fundamentals"
"monolith vs microservices"
"coupling and cohesion"
"modular monolith"
"software architecture trade offs"
```

---

# 11. System Design

### O que é?

É o processo de **projetar um sistema considerando requisitos, escala, performance, dados, custos e falhas**.

É onde todas as áreas anteriores começam a se juntar.

Um processo mental útil:

```text
Requisitos
    ↓
Estimativa de escala
    ↓
Modelo de dados
    ↓
Arquitetura
    ↓
Performance
    ↓
Cache
    ↓
Filas
    ↓
Escalabilidade
    ↓
Confiabilidade
    ↓
Observabilidade
    ↓
Trade-offs
```

### Exemplos de problemas

```text
"Projete um sistema de mensagens."

"Projete um sistema de pagamentos."

"Projete um serviço de armazenamento de imagens."

"Projete um sistema que recebe milhões de requisições."
```

### Buscar

```text
"system design fundamentals"
"system design interview"
"large scale system design"
"designing scalable systems"
```

---

# 12. Cloud e infraestrutura

Depois dos fundamentos, faz sentido entender onde tudo isso é executado.

### Estudar

* Virtual Machines
* Containers
* Docker
* Kubernetes
* Load Balancers
* CDN
* DNS
* Cloud computing
* AWS / Azure / GCP
* Infrastructure as Code

### Buscar

```text
"cloud computing fundamentals"
"Docker fundamentals"
"Kubernetes basics"
"CDN explained"
"load balancer cloud"
```

**Não precisa começar por Kubernetes.**

Primeiro entenda o problema que ele resolve.

---

# 13. Conceitos de arquitetura que valem ouro

Além das tecnologias, existem conceitos que aparecem constantemente.

### Stateless

Um servidor não depende de informações guardadas apenas nele para atender uma requisição.

### Stateful

O servidor mantém estado associado às sessões/processos.

---

### Coupling

Quanto uma parte depende de outra.

> Menor acoplamento geralmente facilita evolução e manutenção.

### Cohesion

O quanto as responsabilidades de um módulo estão relacionadas.

> Alta coesão geralmente é desejável.

---

### Síncrono

```text
A → B → resposta
```

### Assíncrono

```text
A → mensagem → B
```

A pode continuar sem esperar B terminar.

---

### Consistência

Os dados observados pelos diferentes componentes estão de acordo com as regras esperadas.

### Disponibilidade

O sistema está acessível e respondendo quando necessário.

### Durabilidade

Dados confirmados não devem ser perdidos.

---

# 14. O principal: Trade-offs

Essa talvez seja a habilidade mais importante de **System Design**.

Quase nunca existe uma solução perfeita.

Você pode ter que escolher entre coisas como:

```text
Performance
     ↕
Consistência

Simplicidade
     ↕
Flexibilidade

Custo
     ↕
Redundância

Latência
     ↕
Processamento

Complexidade
     ↕
Escalabilidade
```

Então, ao projetar um sistema, não pense apenas:

> "Qual tecnologia devo usar?"

Pense:

> **"Qual problema estou resolvendo e qual custo estou aceitando para resolvê-lo?"**

---

# 📚 O que estudar / ler

## 1. Fundamentos de arquitetura

### *Fundamentals of Software Architecture*

**Mark Richards & Neal Ford**

Bom para aprender a **pensar como arquiteto** e entender trade-offs, estilos arquiteturais e decisões de arquitetura.

---

## 2. Sistemas orientados a dados

### *Designing Data-Intensive Applications*

**Martin Kleppmann**

Um dos livros mais importantes para entender sistemas que lidam com **grandes quantidades de dados, distribuição, replicação, particionamento, processamento e armazenamento**.

É mais denso, então vale deixar para depois dos fundamentos.

---

## 3. System Design

### *System Design Interview*

**Alex Xu**

Bom para praticar problemas de projeto de sistemas e aprender a decompor um problema grande em:

```text
Requisitos
→ Escala
→ API
→ Dados
→ Arquitetura
→ Gargalos
→ Escalabilidade
→ Falhas
```

---

# 🛣️ Ordem de estudo sugerida

Não precisa estudar tudo simultaneamente.

Eu seguiria:

```text
01. HTTP / APIs / Redes
          ↓
02. Banco de Dados
          ↓
03. Performance
          ↓
04. Escalabilidade
          ↓
05. Cache
          ↓
06. Filas e Mensageria
          ↓
07. Arquitetura de Software
          ↓
08. Sistemas Distribuídos
          ↓
09. Confiabilidade
          ↓
10. Observabilidade
          ↓
11. System Design
          ↓
12. Cloud / Infraestrutura
```

---

# 🧠 A pergunta que você deve começar a fazer

Quando encontrar qualquer sistema, tente imaginar:

```text
Quantos usuários?
        ↓
Quantas requisições?
        ↓
Quanto dado?
        ↓
Onde está o gargalo?
        ↓
O que pode falhar?
        ↓
O que precisa escalar?
        ↓
O que pode ser cacheado?
        ↓
O que pode ser assíncrono?
        ↓
Como os dados serão armazenados?
        ↓
Como vou monitorar?
        ↓
Quanto essa solução custa?
```

Esse tipo de raciocínio é, no fundo, o que você está buscando aprender.

---

# 🎯 Resumo final

| Área                      | Pergunta principal                        |
| ------------------------- | ----------------------------------------- |
| **Performance**           | Está rápido o suficiente?                 |
| **Escalabilidade**        | Como suportar crescimento?                |
| **Banco de dados**        | Como armazenar/consultar muitos dados?    |
| **Cache**                 | Como evitar trabalho repetido?            |
| **Mensageria**            | O que pode ser processado depois?         |
| **Sistemas distribuídos** | Como várias máquinas trabalham juntas?    |
| **Confiabilidade**        | O que acontece quando algo falha?         |
| **Observabilidade**       | Como saber o que está acontecendo?        |
| **Arquitetura**           | Como dividir e organizar o sistema?       |
| **Cloud/Infra**           | Onde e como executar tudo isso?           |
| **System Design**         | Como juntar tudo para projetar o sistema? |
| **Trade-offs**            | O que estou ganhando e sacrificando?      |

> **Objetivo final:** sair de
> `"eu sei programar uma funcionalidade"`
> para
> **`"eu consigo pensar em como essa funcionalidade se comporta quando o sistema cresce"`**.

---

### Créditos / referências para estudo

* **Mark Richards & Neal Ford** — *Fundamentals of Software Architecture*
* **Martin Kleppmann** — *Designing Data-Intensive Applications*
* **Alex Xu** — *System Design Interview*
* **UML** — Unified Modeling Language
* Conceitos gerais de **Software Architecture, Distributed Systems, Scalability, Performance e Reliability**
