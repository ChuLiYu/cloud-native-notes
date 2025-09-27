---
title: Distributed Systems in One Lesson — Notes (English)
tags: [distributed-systems, storage, computation, messaging, english]
updated: 2025-09-27
---

# Distributed Systems in One Lesson — Notes (Tim Berglund)

## 1. What is a Distributed System?
A **collection of independent computers** that **appears as a single system** to users.

**Core properties:**
- **Concurrency**: multiple nodes execute simultaneously.  
- **Independent failure**: any node can fail on its own.  
- **No global clock**: clocks are **not perfectly synchronized**, making time and ordering tricky.  

---

## 2. The Three Topics
- **Storage**  
- **Computation**  
- **Messaging**  

---

## 3. Storage

### 3.1 Single-Master Storage
- One primary database handles all **reads and writes**.  
- Guarantees **strong consistency** (read-after-write).  
- Limitation: bottleneck once the primary cannot scale further.  

### 3.2 Read Replication
- **Leader/Follower** pattern: writes go to leader, followers replicate.  
- **Pros**: scales read throughput.  
- **Cons**: eventual consistency, stale reads possible.  

### 3.3 Sharding
- Split data by **shard key** (e.g., user ID ranges).  
- **Pros**: scales writes and dataset size.  
- **Cons**: cross-shard joins are expensive, often require **denormalization**.  

### 3.4 Consistent Hashing
- Keys hashed onto a **hash ring** → assigned to nodes.  
- Supports **elastic scaling**: adding/removing nodes moves only a subset of keys.  

### 3.5 Quorum & Tunable Consistency
- With replication factor `N`:  
  - Require `W` nodes to confirm a write.  
  - Require `R` nodes to confirm a read.  
  - **Rule**: `R + W > N` ensures strong consistency.  

### 3.6 CAP Theorem
- Cannot simultaneously achieve **Consistency (C)**, **Availability (A)**, and **Partition tolerance (P)**.  
- In a partition:  
  - **CP system**: sacrifices availability, keeps consistency.  
  - **AP system**: sacrifices consistency, stays available.  

---

## 4. Computation

### 4.1 MapReduce
- **Map → Shuffle → Reduce**.  
- Example: word count.  
- **Pros**: batch scalability.  
- **Cons**: high latency, developer-unfriendly.  

### 4.2 Hadoop vs Spark
- **Hadoop**: batch-oriented, tied to HDFS.  
- **Spark**: faster, storage-agnostic, provides RDD/Dataset APIs.  

### 4.3 Stream Processing
- Process **data in motion** instead of after storage.  
- Tools: **Kafka Streams, Flink** → enable **low latency, real-time** analytics.  

### 4.4 Lambda Architecture (anti-pattern)
- Maintains both batch and stream paths.  
- Issues: duplicate logic, higher complexity.  
- Modern trend: unified stream-first architecture.  

---

## 5. Messaging

### 5.1 Why Messaging?
- Enables **loose coupling** in microservices.  
- Avoids shared-database bottlenecks.  

### 5.2 Kafka — Key Concepts
- **Message**: single event or record.  
- **Topic**: append-only log of messages.  
- **Producer**: writes events to a topic.  
- **Consumer**: reads events from a topic.  
- **Broker**: Kafka server node.  

### 5.3 Partitioning & Ordering
- Topics split into **partitions**.  
- Guarantees **ordering within a partition**, not across partitions.  
- **Keyed partitioning** ensures related events are ordered.  

### 5.4 Replication & Fault Tolerance
- Partitions replicated across brokers.  
- **Leader election** handles broker failures.  

### 5.5 Consumer Groups
- Consumers coordinate to share partitions.  
- Offsets track progress, enabling **replay**.  

### 5.6 Delivery Semantics
- **At-least-once**: default, may cause duplicates.  
- **Exactly-once**: possible with idempotent producers + transactions.  

### 5.7 Retention & Event Log
- Retention based on **time, size, or compaction**.  
- Stored events can be **replayed** to rebuild state or bootstrap new services.  

---

## 6. Key Takeaways
- Distributed systems enable scale but introduce **trade-offs**.  
- Critical to understand **consistency, latency, and failure modes**.  
- Purpose-built tools:  
  - **Cassandra / DynamoDB** → storage  
  - **Spark / Flink** → computation  
  - **Kafka** → messaging  

---

## 📚 References
- Tim Berglund — *Distributed Systems in One Lesson*  
- [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)  
- [Jepsen: Consistency Testing](https://jepsen.io/)  
- [Kafka Documentation](https://kafka.apache.org/documentation/)  
