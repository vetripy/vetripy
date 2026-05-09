# Vetrivel M

Backend engineer at Fidelity Investments, working on the infrastructure 
that keeps trading platforms running. My day job involves low-latency APIs, 
event-driven architectures, and distributed systems.

Outside of work, I build things to go deeper, the kind of projects that force you to actually understand how exchanges, 
trading systems, and financial infrastructure work under the hood.

---

## What I Work With

**Core:** Java, Spring Boot, REST APIs, Microservices  
**Messaging:** Apache Kafka, Aeron  
**Infrastructure:** Docker, Kubernetes, AWS (Lambda, SQS, Step Functions)  
**Protocols:** QuickFIX/J (FIX Protocol), SBE (Simple Binary Encoding)    
**Databases:** PostgreSQL, MongoDB    
**Observability:** Datadog, Grafana   
**CI/CD and Other tools**: Jenkins, Sonar

---

## What I've Built at Fidelity

I can't open-source production code, but here's what I actually work on:

- **Order Entry API** — REST endpoints for a live trading platform, 
  sub-100ms latency, horizontally scaled for high availability
- **Market Access Gateway** — Built from scratch to handle communication 
  between liquidity venues and our trading platform using QuickFIX
- **Market Data Endpoints** — Consume upstream feeds, aggregate in real-time, 
  serve clients on a low-latency platform
- **Matching Engine** — Currently working on microsecond-level benchmarking 
  and performance profiling
- **Test Automation Suite** — Cucumber + Jenkins pipeline that cut a full 
  sprint cycle of manual testing to a 10-minute CI run

---

## Featured Project — Mini Exchange Engine

> A deterministic, in-memory matching engine built in pure Java.  
> A real attempt to understand how exchanges 
> actually process orders.

**What it does:**
- Matches orders using price-time priority (the same model real exchanges use)
- Supports Limit, Market, IOC, and Fill-or-Kill order types
- Event-sourced design — every state change is a TradeEvent or OrderUpdateEvent
- Command-based input — NewOrderCommand, CancelOrderCommand
- Runs in both SYNC and ASYNC modes

**Why the architecture decisions matter:**

The engine uses a single-threaded deterministic loop — the same design 
philosophy behind LMAX Disruptor and most high-performance exchange cores. 
Concurrency bugs in matching engines cause incorrect fills and financial loss. 
Single-threaded + sequenced = provably correct.

Key structures:
- `TreeMap` for buy/sell books — price-sorted, O(log n) insertion
- `HashMap` for order index — O(1) lookups by order ID
- `LinkedHashSet` at each price level — FIFO queue for time priority
- `MatchContext` — atomically collects all events produced by a single command

**What I'm working on next:**
- Microsecond benchmarking with JMH
- Ring buffers instead of BlockingQueues

[View the project →](https://github.com/yourusername/mini-exchange-engine)

---

## Other Projects

**FastAPI Event Management API**  
REST API for a real-world event management system — CRUD operations, 
built with FastAPI and Python. Backend complete, UI in progress.  
[View →](https://github.com/vetripy/starvoirs-api)

**College Bus Tracker**  
Real-time bus tracking for college routes using Django and Google Maps API.  
Built during college, but the problem was real — students had no visibility 
on bus locations.  
[View →](https://github.com/vetripy/BusTracker)

---

## What I'm Exploring Right Now

- Microsecond-level latency profiling in Java (JMH, async-profiler)
- LMAX Ring Buffers
- Order matching algorithms and exchange microstructure

---

## Let's Talk

If you're building something in trading infrastructure, exchange systems, 
or serious backend work — I'm always open to a conversation.

[LinkedIn](https://www.linkedin.com/in/vetrivel-m-458a3a1b7/) · 
[Email](mailto:vetrisurabi@gmail.com)
