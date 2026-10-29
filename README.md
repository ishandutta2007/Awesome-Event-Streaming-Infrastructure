# Awesome-Event-Streaming-Infrastructure

# Top Event Streaming Infrastructure Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Distributed Logs, Real-Time Data Pipelines & Self-Hosted Streaming Platforms*  
**Last updated: October 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Event Streaming Infrastructure**. These tools enable organizations to capture, store, process, and replay continuous streams of events—clickstreams, logs, transactions, telemetry—acting as the central nervous system for real-time applications and event-driven architectures.

**Examples** include Shopify Monorail, Apache Kafka (Confluent), Apache Pulsar (StreamNative), Amazon Kinesis, Google Cloud Pub/Sub, Azure Event Hubs, Redpanda, Decodable, Upstash Kafka, and IBM Event Streams (the category leaders).

**Open-source emphasis**: Event Streaming is a domain where open-source tooling is **foundational and production-proven**. **Apache Kafka** remains the de facto standard, with a massive ecosystem (Kafka Connect, Kafka Streams, ksqlDB) and the broadest tooling depth . **Apache Pulsar** offers a compelling alternative with native multi-tenancy, compute/storage separation via BookKeeper, and built-in geo-replication, though its ecosystem is smaller . **Redpanda** provides a Kafka-compatible broker rewritten in C++ (no JVM, no ZooKeeper) for lower latency and operational simplicity, with real-world cases showing 5-6x fewer resources and single-digit millisecond latency . **NATS** serves lightweight messaging needs. The landscape is also evolving with edge-native experiments like **kafka.do** (Kafka-compatible on Cloudflare Workers) . The critical caveat: IBM acquired Confluent in March 2026, consolidating vendor options , and Kafka's own 4.0 release removed ZooKeeper entirely (KRaft only) .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Shopify Monorail](https://shopify.engineering/)**  
  Shopify's internal event streaming infrastructure (not a public product) built for high-volume commerce events; represents the scale and reliability requirements of a major platform's event backbone.

- **[Confluent Cloud (Apache Kafka)](https://www.confluent.io/)**  
  Fully managed Kafka service with Schema Registry, Kafka Connect, ksqlDB, and Stream Governance; now part of IBM following the March 2026 acquisition . The most mature managed Kafka offering with the deepest ecosystem.

- **[StreamNative Cloud (Apache Pulsar)](https://streamnative.io/)**  
  Managed Pulsar service built on the URSA engine; offers native Pulsar protocol with built-in multi-tenancy, geo-replication, and multi-protocol support (Pulsar, Kafka via KSN, MQTT via MoP, REST) . Kafka Service is also available for Kafka workloads.

- **[Amazon Kinesis](https://aws.amazon.com/kinesis/)**  
  AWS's serverless streaming service with shard-based provisioning; strict per-shard ordering and Enhanced Fan-Out for low-latency consumers. Best for AWS-native event-driven architectures .

- **[Google Cloud Pub/Sub](https://cloud.google.com/pubsub)**  
  Fully serverless, globally auto-sharding message queue with no partition provisioning required; strong for unpredictable traffic and zero-ops pipelines, with P99 latency around 32ms at 50K msg/s .

- **[Azure Event Hubs](https://azure.microsoft.com/en-us/products/event-hubs)**  
  Azure's event streaming platform with native Kafka protocol compatibility, throughput units, and integration with the Azure ecosystem; a common choice for hybrid cloud and Kafka-compatible workloads on Azure .

- **[Redpanda Cloud](https://redpanda.com/)**  
  Managed Redpanda service with BYOC (Bring Your Own Cloud) deployment options; provides Kafka-compatible API with lower operational overhead and lower latency than JVM-based Kafka .

- **[Decodable](https://www.decodable.co/)**  
  Managed stream processing platform built on Apache Flink; connects to Kafka, Pulsar, and other sources for real-time ETL and event-driven applications.

- **[Upstash Kafka](https://upstash.com/kafka)**  
  Serverless Kafka with pay-per-message pricing and REST API; designed for serverless and edge applications needing lightweight Kafka access without cluster management.

- **[IBM Event Streams](https://www.ibm.com/products/event-streams)**  
  IBM's enterprise Kafka distribution with additional security, management, and integration capabilities; positioned for IBM Cloud and hybrid enterprise deployments.

## Open-Source GitHub Projects

### Distributed Logs & Streaming Platforms

- **[Apache Kafka](https://github.com/apache/kafka)**  
  The foundational open-source event streaming platform (Apache 2.0); distributed, partitioned, replicated commit log with the broadest ecosystem including **Kafka Connect**, **Kafka Streams**, and **ksqlDB** . **Kafka 4.0 removed ZooKeeper entirely**—all 4.x deployments use KRaft mode for simpler operations . Kafka remains the safest choice when you need sustained high throughput, long-horizon replay, and the deepest tooling/connector ecosystem .

- **[Apache Pulsar](https://github.com/apache/pulsar)**  
  Open-source distributed pub/sub messaging and streaming platform (Apache 2.0) with **native multi-tenancy** (tenant/namespace isolation), **separate compute and storage layers** (brokers + BookKeeper), and **built-in geo-replication** . Supports both streaming (log-centric) and messaging (queue-like) semantics, making it suitable for workloads needing both patterns in one system . Trade-offs: smaller ecosystem than Kafka, additional infrastructure components (BookKeeper), and a steeper learning curve .

- **[Redpanda](https://github.com/redpanda-data/redpanda)**  
  Kafka-compatible streaming platform written in C++ using the Seastar framework (thread-per-core, no JVM, no ZooKeeper) . Provides **lower and more predictable latency** (no GC pauses) and **lower operational overhead** (single binary) than JVM-based Kafka. Real-world cases: StoneX achieved 5-6x fewer resources and single-digit millisecond latency after migrating from Kafka ; Equal Experts hit 5ms latency for real-time alerting . **Community Edition uses BSL 1.1** (converts to Apache 2.0 after 4 years); Enterprise features (tiered storage, etc.) require commercial license . **Not fully drop-in**—edge cases exist around Kafka Streams and some connector configurations .

- **[NATS](https://github.com/nats-io/nats-server)**  
  Lightweight, high-performance messaging system (Apache 2.0) with built-in pub/sub, request-reply, and queue groups . **Not a Kafka replacement**—it excels at low-latency messaging and service communication rather than durable event log replay. Best for microservices communication and IoT edge scenarios where simplicity and speed matter more than long retention.

### Edge-Native & Experimental

- **[kafka.do](https://github.com/dot-do/kafka)**  
  Kafka-compatible streaming platform on **Cloudflare Workers with Durable Objects** (MIT) . Uses SQLite for hot data, R2 for warm/cold archives, and runs at the edge globally. **Early-stage/experimental**—supports Kafka wire protocol for most clients but not a production-grade replacement for Kafka or Redpanda. Interesting for edge-native streaming experiments.

### Additional Strong Open-Source Options

- **Apache Flink** — Open-source stream processing framework (Apache 2.0); pairs with Kafka/Pulsar for stateful computations, event-time processing, and exactly-once semantics. The standard for complex stream processing .
- **Apache BookKeeper** — The storage layer underlying Pulsar; also usable standalone for durable, replicated log storage .
- **AutoMQ** — Open-source Kafka-compatible platform using object storage (S3) for cost efficiency; a BYOC option for Azure/AWS deployments .

**Frameworks for building custom systems**: For **maximum ecosystem and tooling depth**, Kafka with KRaft (4.x) is the safe standard . For **multi-tenancy and geo-replication in one system**, Pulsar . For **lower latency and operational simplicity with Kafka compatibility**, Redpanda . For **lightweight microservice messaging**, NATS . For **managed services**, Confluent Cloud (Kafka), StreamNative (Pulsar), or Redpanda Cloud depending on protocol and deployment preferences.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Event streaming platforms handling production data must comply with applicable security policies and data governance requirements; retention policies and access controls are critical for compliance-sensitive workloads.
- **Open-source event streaming is mature and production-proven**—Kafka and Pulsar are battle-tested at massive scale, and Redpanda provides a compelling Kafka-compatible alternative with lower operational overhead . However, **operational complexity varies significantly**: Kafka with KRaft is simpler than legacy ZooKeeper deployments but still requires expertise; Pulsar adds BookKeeper management; Redpanda reduces overhead but has a smaller ecosystem . Choose based on team skills and workload patterns, not benchmarks alone .
- Verify license terms for commercial use; Kafka and Pulsar use Apache 2.0, Redpanda Community uses BSL 1.1 (converts to Apache 2.0), and NATS uses Apache 2.0.

---

**Made for platform engineers, data infrastructure teams, and real-time application architects.**  
Let's make event streaming more open, but with clear eyes about the operational trade-offs between ecosystem depth, latency, and simplicity.
