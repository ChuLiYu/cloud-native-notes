# Distributed Systems in One Lesson — Notes (Tim Berglund)

## What is a Distributed System?
A **collection of independent computers** that **appears as a single system** to users.

**Core properties:**
- **Concurrency**: many nodes run at the same time.  
- **Independent failure**: any node can fail on its own.  
- **No global clock**: clocks are **not perfectly synchronized**, so time/order is tricky.  

---

## The 3 Topics
- **Storage**
- **Computation**
- **Messaging**

---

## 1) Storage

### 1.1 Single-Master Storage
- One primary database handles **reads/writes**.  
- **Strong consistency** (read-after-write).  
- Scales **until** the single node becomes a bottleneck.  

### 1.2 Read Replication
- **Leader/Follower**: writes go to leader, followers replicate.  
- Pros: scales **reads**.  
- Cons: **eventual consistency** (stale reads possible).  

### 1.3 Sharding
- Split data by **shard key** (e.g., username ranges).  
- Pros: scales **writes** and data size.  
- Cons: **cross-shard joins** hard/expensive → often need **denormalization**.  

### 1.4 Consistent Hashing
- Hash key → map onto **hash ring** → store on responsible node(s).  
- Supports **elastic growth** (adding/removing nodes moves few keys).  

### 1.5 Quorum & Tunable Consistency
- With replication factor `N`:  
  - Require `W` nodes for write, `R` nodes for read.  
  - **Rule:** `R + W > N` ⇒ strong consistency.  

### 1.6 CAP Theorem
- Cannot have all **Consistency (C)**, **Availability (A)**, **Partition tolerance (P)**.  
- In a partition:  
  - **CP system** rejects some requests to stay consistent.  
  - **AP system** serves stale data but stays available.  

---

## 2) Computation

### 2.1 MapReduce
- **Map → Shuffle → Reduce**.  
- Classic **word count** example.  
- Pros: scales batch jobs.  
- Cons: high latency, hard to program.  

### 2.2 Hadoop vs Spark
- **Hadoop**: batch-oriented, tied to HDFS.  
- **Spark**: higher-level APIs (RDD/Dataset), storage-agnostic, faster & easier for devs.  

### 2.3 Stream Processing
- Compute on **data in flight**, not only after storage.  
- Kafka Streams, Flink → **low latency, real-time** analytics.  

### 2.4 Lambda Architecture (anti-pattern)
- Dual path: batch + stream.  
- Problem: duplicate logic.  
- Trend: unify with modern stream frameworks.  

---

## 3) Messaging

### 3.1 Why Messaging
- Enables **loose coupling** in microservices.  
- Avoids shared-database bottleneck.  

### 3.2 Kafka — Key Concepts
- **Message**: event/record.  
- **Topic**: named log of messages.  
- **Producer**: writes to topic.  
- **Consumer**: reads from topic.  
- **Broker**: Kafka server node.  

### 3.3 Partitioning & Ordering
- Topic split into **partitions**.  
- Guarantees **ordering within partition**, not globally.  
- Use **keyed partitioning** to keep related events ordered.  

### 3.4 Replication & Fault Tolerance
- Partitions replicated across brokers.  
- **Leader election** if one broker fails.  

### 3.5 Consumer Groups
- Consumers share partitions for **parallelism**.  
- Offsets track progress (allow **replay**).  

### 3.6 Delivery Semantics
- **At-least-once** (default, may see duplicates).  
- **Exactly-once** possible with idempotent producers & transactions.  

### 3.7 Retention & Event Log
- Topics can keep data for **time/size/compaction**.  
- Events can be **replayed** to rebuild state or feed new services.  

---

## Key Takeaways
- Distributed systems scale but force **trade-offs**.  
- Know your **consistency, latency, failure** choices.  
- Use purpose-built tools: **Cassandra (storage)**, **Spark (compute)**, **Kafka (messaging)**.  

