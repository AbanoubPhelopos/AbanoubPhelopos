
<p align="center">
  <a href="https://linkedin.com/in/abanoub-saweris"><code>🔗 LinkedIn</code></a> &nbsp;&nbsp;
  <a href="https://github.com/AbanoubPhelopos"><code>💻 GitHub</code></a> &nbsp;&nbsp;
  <a href="mailto:abanoub.saweris02@gmail.com"><code>📧 Email</code></a> &nbsp;&nbsp;
  <a href="https://codeforces.com/profile/__PoP__"><code>⚡ Codeforces</code></a> &nbsp;&nbsp;
  <a href="https://leetcode.com/u/Abanoub-Saweris"><code>🧩 LeetCode</code></a> &nbsp;&nbsp;
  <a href="tel:+201274782728"><code>📱 +20 127 478 2728</code></a>
</p>

<br/>

## 🧬 Who Am I

> *I don't just write backends — I engineer distributed systems that survive real traffic at scale.*

I am a Software Engineer specializing in high-performance architectures, event-driven microservices, and robust cloud-native infrastructures. I bring competitive programming precision to designing rock-solid production environments.

```
📍 Cairo, Egypt
🎓 B.Sc. Computer Science @ Ain Shams University
🏆 Codeforces Specialist · 1,000+ problems solved
👨‍🏫 Mentored 20+ software engineering students @ IClub
```

<br/>

---

## 🛸 Tech Stack Universe

| Category | Tools & Technologies |
|:---|:---|
| **Languages** | `C#` · `Python` · `C++` · `TypeScript` · `Java` · `Go` · `SQL` |
| **Frameworks & Libraries** | `ASP.NET Core` · `EF Core` · `SignalR` · `gRPC` · `MediatR` · `MassTransit` · `Wolverine` · `Ocelot` · `LINQ` · `Dapper` |
| **Data & Messaging** | `PostgreSQL` · `SQL Server` · `MongoDB` · `Redis` · `RabbitMQ` |
| **Cloud & DevOps** | `Docker` · `Kubernetes` · `Helm` · `ArgoCD` · `GitHub Actions` · `Nginx` |
| **Observability** | `Prometheus` · `Grafana` · `Loki` · `Promtail` · `OpenTelemetry` |
| **Architectures** | `Microservices` · `Clean Architecture` · `Vertical Slice` · `CQRS` · `Event-Driven` · `Saga / Outbox` · `OAuth2 / OIDC` · `REST` |

<br/>

---

## 🔩 Open Source Projects

### 🛍️ [E-Commerce Microservices](https://github.com/AbanoubPhelopos/E-Commerce)
A production-grade distributed e-commerce platform featuring 10+ decoupled microservices with real-time analytics.

<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <h4>⚙️ Architecture & Features</h4>
      <ul>
        <li><b>10 ASP.NET Core 10</b> microservices orchestrated behind <b>Nginx</b> & <b>Ocelot Gateway</b> using Clean Architecture & CQRS via MediatR.</li>
        <li><b>Polyglot Persistence:</b> MongoDB (Catalog), Redis (Basket), PostgreSQL + Dapper (Discount), SQL Server + EF Core (Ordering, Payment, Notification, UserManagement, Admin).</li>
        <li><b>Real-time Analytics:</b> Admin Dashboard consuming <b>Apache Kafka</b> events with live updates via <b>SignalR</b>.</li>
        <li><b>AI Shopping Assistant:</b> Conversational AI powered by <b>MiniMax M2.7</b> with semantic product search using embeddings.</li>
        <li><b>Async Saga Flow:</b> Robust async checkout orchestrations via <b>MassTransit + RabbitMQ</b> integrated with <b>Stripe Payments</b>.</li>
        <li><b>Security:</b> Enforced by Duende IdentityServer (OAuth2 / OIDC) and Redis-backed custom idempotency middlewares.</li>
        <li><b>Event-Driven Architecture:</b> RabbitMQ for service-to-service communication, Kafka for analytics event streaming.</li>
      </ul>
      <br/>
      <h4>🛠️ Tools & Stack</h4>
      <code>C#</code> · <code>ASP.NET Core 10</code> · <code>SignalR</code> · <code>Confluent.Kafka</code> · <code>MassTransit</code> · <code>RabbitMQ</code> · <code>Redis</code> · <code>PostgreSQL</code> · <code>SQL Server</code> · <code>MongoDB</code> · <code>Duende IdentityServer</code> · <code>gRPC</code> · <code>MiniMax AI</code> · <code>SendGrid</code>
    </td>
    <td width="50%" valign="center">
      <img src="assets/ecommerce_mockup.png" alt="E-Commerce Analytics" width="100%" style="border-radius: 8px;" />
    </td>
  </tr>
</table>

```mermaid
flowchart TD
    subgraph Gateway["🌐 API Gateway"]
        GW[Nginx + Ocelot<br/>:44344]
    end
    subgraph Services["🔧 Microservices"]
        CAT[📦 Catalog<br/>MongoDB :8080]
        BAS[🛒 Basket<br/>Redis :8081]
        DIS[🏷️ Discount<br/>PostgreSQL :8082]
        ORD[📋 Ordering<br/>SQL Server :8083]
        PAY[💳 Payment<br/>Stripe :8084]
        USR[👥 UserManagement<br/>SQL Server :8086]
        NOT[📧 Notification<br/>SendGrid :8087]
        AST[🤖 Assistant<br/>MiniMax AI :8088]
        ADM[📊 Admin Dashboard<br/>Kafka + SignalR :8089]
    end
    subgraph Infra["⚙️ Infrastructure"]
        MQ[🐰 RabbitMQ]
        IS[🔐 IdentityServer<br/>:9001]
        RD[🔴 Redis Idempotency]
        KAF[🟠 Kafka]
    end

    GW --> CAT
    GW --> BAS
    GW --> ORD
    GW --> PAY
    GW --> USR
    GW --> NOT
    GW --> AST
    GW --> ADM
    
    BAS -->|MassTransit Saga| MQ
    MQ --> ORD
    ORD --> MQ
    MQ --> PAY
    MQ --> NOT
    MQ --> AST
    
    ADM --> KAF
    KAF -.->|Events| ADM
    ADM -.->|SignalR| GW
    
    DIS ---|gRPC| BAS
    AST -->|Semantic Search| CAT
    AST -->|Recommendations| CAT
    
    IS -.->|OAuth2 / OIDC| GW
    RD -.->|Dedup| Services

    style Gateway fill:#0d1117,stroke:#58a6ff,color:#c9d1d9
    style Services fill:#0d1117,stroke:#a78bfa,color:#c9d1d9
    style Infra fill:#0d1117,stroke:#f97316,color:#c9d1d9
```

<br/>

### 📑 [TailorCV](https://github.com/AbanoubPhelopos/TailorCV)
An AI-powered professional resume tailoring platform that matches candidate profiles with custom scrapers.

<table width="100%">
  <tr>
    <td width="50%" valign="center">
      <img src="assets/tailor_cv_mockup.png" alt="TailorCV Dashboard" width="100%" style="border-radius: 8px;" />
    </td>
    <td width="50%" valign="top">
      <h4>⚙️ System Internals</h4>
      <ul>
        <li><b>Modular Monolith</b> designed with <b>Vertical Slice Architecture</b> in .NET 10 with CQRS pattern.</li>
        <li>Strict module isolation with distinct PostgreSQL databases schema-boundaries.</li>
        <li>Hybrid communication using <b>Wolverine + RabbitMQ</b> for outbox transactions/sagas, and <b>gRPC</b> for high-speed synchronous reads.</li>
        <li>Data pipeline utilizing <b>OpenAI API</b> for parsing/parsing, <b>Playwright</b> for automated job scraping, and <b>Puppeteer</b> for rendering PDF resumes.</li>
      </ul>
      <br/>
      <h4>🛠️ Tools & Stack</h4>
      <code>C#</code> · <code>.NET 10</code> · <code>Wolverine</code> · <code>RabbitMQ</code> · <code>gRPC</code> · <code>PostgreSQL</code> · <code>OpenAI API</code> · <code>Playwright</code> · <code>Puppeteer</code>
    </td>
  </tr>
</table>

```mermaid
flowchart LR
    A[📄 Upload Resume] --> B[OpenAI Parser]
    B --> C[(PostgreSQL<br/>Per-Module Schemas)]
    D[🌐 Playwright Scraper] --> E[Job Listings]
    E --> F[Semantic Matcher]
    B --> F
    F --> G[Puppeteer PDF]
    G --> H[📑 Tailored CV]

    C <-->|Wolverine + RabbitMQ<br/>Outbox & Sagas| F
    E <-->|gRPC Sync| C

    style A fill:#0d1117,stroke:#10b981,color:#c9d1d9
    style H fill:#0d1117,stroke:#10b981,color:#c9d1d9
```

<br/>

### 🗺️ [Wsnly](https://github.com/AbanoubPhelopos/Wsnly-Backend)
An AI-powered multimodal transit routing and query optimization system for Greater Cairo's public transportation network.

<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <h4>⚙️ Architecture & Features</h4>
      <ul>
        <li><b>Polyglot Microservices:</b> Django API gateway + Python AI service + C++ routing engine orchestrated via <b>gRPC</b>.</li>
        <li><b>Smart Routing:</b> A* pathfinding over in-memory GTFS graph (~646 stops, ~242K polyline points) computing routes in <15ms.</li>
        <li><b>NLP Extraction:</b> Custom Arabic/English NER pipeline + Google Maps geocoding for natural language trip queries.</li>
        <li><b>Multi-Option Routes:</b> Returns optimal, bus-only, metro-only, and microbus alternatives with fare estimation.</li>
        <li><b>Real-time Analytics:</b> Admin dashboard with route statistics, user growth tracking, and feedback analytics.</li>
        <li><b>Transit Data API:</b> Nearby stops, line details with ordered stops, and GTFS polylines for map rendering.</li>
      </ul>
      <br/>
      <h4>🛠️ Tools & Stack</h4>
      <code>C++</code> · <code>Python</code> · <code>Django</code> · <code>DRF</code> · <code>gRPC</code> · <code>A* Search</code> · <code>NLP</code> · <code>GTFS</code> · <code>PostgreSQL</code> · <code>Redis</code> · <code>Google Maps API</code>
    </td>
    <td width="50%" valign="center">
      <img src="assets/wsnly_mockup.png" alt="Wsnly Optimization" width="100%" style="border-radius: 8px;" />
    </td>
  </tr>
</table>

```mermaid
flowchart TD
    subgraph Client["🖥️ Client (Web / Mobile)"]
        WEB[🌐 Browser]
        MOB[📱 Mobile App]
    end

    subgraph Gateway["🐍 Wslny API (Django + DRF)"]
        AUTH[🔐 Auth Layer<br/>JWT + OAuth]
        ORCH[🎯 Orchestrator<br/>Route Coordination]
        ADMIN[📊 Admin Panel<br/>Analytics]
    end

    subgraph Services["⚙️ Application Services"]
        AI[🤖 AI Service<br/>Python + gRPC<br/>Port 50052]
        ROUTING[⚡ RoutingEngine<br/>C++ + gRPC<br/>Port 50051]
    end

    subgraph Infra["📦 Infrastructure"]
        PG[("🗄️ PostgreSQL<br/>Port 5432")]
        REDIS[("📦 Redis<br/>Port 6379")]
    end

    WEB & MOB -->|"HTTP/JSON<br/>JWT Bearer"| AUTH
    AUTH --> ORCH
    ORCH --> ADMIN

    ORCH --> |"gRPC<br/>Text Flow"| AI
    ORCH --> |"gRPC<br/>All Flows"| ROUTING

    ORCH --> PG
    ORCH --> REDIS

    AI --> |"ExtractRoute()"| ORCH
    ROUTING --> |"GetRoute()<br/>4 options"| ORCH

    style Client fill:#0d1117,stroke:#58a6ff,color:#c9d1d9
    style Gateway fill:#0d1117,stroke:#a78bfa,color:#c9d1d9
    style Services fill:#0d1117,stroke:#f97316,color:#c9d1d9
    style Infra fill:#0d1117,stroke:#10b981,color:#c9d1d9
```

---

### ☁️ [Event Management System](https://github.com/6-Brain-Cells/event-management-cloud)
A high-availability, production-grade cloud-native platform.

<table width="100%">
  <tr>
    <td width="50%" valign="center">
      <img src="assets/event_mockup.png" alt="Event Management Cloud Architecture" width="100%" style="border-radius: 8px;" />
    </td>
    <td width="50%" valign="top">
      <h4>⚙️ Architecture & Features</h4>
      <ul>
        <li><b>Decoupled Microservices:</b> 4 high-performance services built with <b>FastAPI</b> (User, Event, Registration, Notification) orchestrated behind an <b>Nginx API Gateway</b>.</li>
        <li><b>Resilient Communication:</b> Dynamic inter-service circuit breakers, topic-based routing with Dead Letter Queues (DLQ) in <b>RabbitMQ</b>, and version-based optimistic concurrency controls on PostgreSQL.</li>
        <li><b>Distributed Caching:</b> High-speed token storage and event response caching using <b>Redis</b> with automated TTL eviction.</li>
        <li><b>GitOps & Cloud-Native Deployment:</b> Containerized with multi-stage Docker builds, deployed on <b>Kubernetes</b> via custom <b>Helm</b> charts, and fully managed using <b>ArgoCD</b>.</li>
        <li><b>Observability Pipeline:</b> Complete telemetry stack integrating <b>Prometheus</b> metrics, <b>Loki</b> log aggregation, and custom <b>Grafana</b> dashboards.</li>
      </ul>
      <br/>
      <h4>🛠️ Tools & Stack</h4>
      <code>Python</code> · <code>FastAPI</code> · <code>RabbitMQ</code> · <code>Redis</code> · <code>PostgreSQL</code> · <code>Nginx</code> · <code>Kubernetes</code> · <code>Helm</code> · <code>ArgoCD</code> · <code>Prometheus</code> · <code>Grafana</code> · <code>Loki</code>
    </td>
  </tr>
</table>

```mermaid
flowchart TD
    subgraph Client["🖥️ Client Layer"]
        B[🌐 Browser / API Client]
    end

    subgraph Gateway["🚪 API Gateway"]
        NG[Nginx Reverse Proxy<br/>Rate Limiting & Auth]
    end

    subgraph Services["⚙️ Microservices"]
        US[👤 User Service<br/>FastAPI :8001]
        ES[📅 Event Service<br/>FastAPI :8002]
        RS[🎫 Registration Service<br/>FastAPI :8003]
        NS[🔔 Notification Service<br/>FastAPI :8004]
    end

    subgraph Messaging["📡 Message Broker"]
        MQ[🐰 RabbitMQ Topic Exchange]
        DLQ[Dead Letter Queue]
    end

    subgraph DB["🗄️ Database & Cache"]
        PG[(🐘 PostgreSQL)]
        RD[(📡 Redis Cache)]
    end

    subgraph Telemetry["📊 Observability"]
        PROM[Prometheus Scrapers]
        GRAF[Grafana Dashboards]
    end

    B --> NG
    NG --> US & ES & RS & NS
    
    RS -->|Circuit Breaker| ES
    US & ES & RS -->|Publish| MQ
    MQ -->|Consume| NS
    MQ -.->|Failure| DLQ

    US & ES & RS & NS --> PG
    US & ES & RS --> RD
    
    US & ES & RS & NS -.->|Metrics| PROM
    PROM --> GRAF

    style Client fill:#0d1117,stroke:#58a6ff,color:#c9d1d9
    style Gateway fill:#0d1117,stroke:#a78bfa,color:#c9d1d9
    style Services fill:#0d1117,stroke:#f97316,color:#c9d1d9
    style DB fill:#0d1117,stroke:#10b981,color:#c9d1d9
    style Messaging fill:#0d1117,stroke:#e94560,color:#c9d1d9
    style Telemetry fill:#0d1117,stroke:#a78bfa,color:#c9d1d9
```

---

### 💻 [FOS — FCIS Operating System](https://github.com/fcisProjects/FOS)
A fully modular OS Kernel written from scratch to learn micro-level system operations.

- **Memory management:** Custom dynamic allocator supporting First-Fit / Best-Fit algorithms, fully functional virtual memory page table paging, and an **Nth Chance Clock** page eviction scheduler.
- **Process scheduling:** Implemented Process tables, custom pre-emptive **Priority Round-Robin** scheduler, and synchronisation primitives (SpinLocks, sleep locks, semaphores).
- **🛠️ Tools & Stack:** `C` · `Assembly` · `OS Architecture` · `Paging` · `System Schedulers` · `Kernel Primitives`

<br/>


<h3 align="center">Let's build something that scales 🚀</h3>

<p align="center">
  <a href="mailto:abanoub.saweris02@gmail.com">abanoub.saweris02@gmail.com</a> &nbsp;·&nbsp;
  <a href="https://linkedin.com/in/abanoub-saweris">LinkedIn</a> &nbsp;·&nbsp;
  <a href="https://codeforces.com/profile/__PoP__">Codeforces</a> &nbsp;·&nbsp;
  <a href="tel:+201274782728">+20 127 478 2728</a>
</p>
