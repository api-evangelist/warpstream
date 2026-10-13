<!-- fetched 2026-10-13 from https://docs.warpstream.com/warpstream/reference/protocol-and-feature-support by sweep-shape-compat.py; text extracted from the provider's own page -->

Protocol and Feature Support | WarpStream 
 ⌘ Ctrl k 
 WarpStream.com Slack Discord Contact Us Create Account More 
 GitBook Assistant
 I'm here to help you with the docs.
 What is this page about? What should I read next? Can you give an example? 
 ⌘ Ctrl i 
 AI Based on your context 
 Send 
 Overview 
 Introduction 
 Architecture 
 Change Log 
 Getting Started 
 Install the WarpStream Agent / CLI 
 Run the Agents Locally 
 "Hello World" for Apache Kafka 
 Agent Setup 
 Deploy the Agents 
 Object Storage Configuration 
 Set up Monitoring 
 Infrastructure as Code 
 Kafka 
 Configure Clients 
 Manage Security 
 Manage Connectors 
 Deploy (advanced) 
 Reference Compression 
 Protocol and Feature Support Kafka vs WarpStream Configuration Reference 
 Compacted topics 
 Broker Configuration Reference 
 Topic Configuration Reference 
 HTTP Endpoints 
 Partitions Auto-Scaler 
 Serverless Clusters 
 Partition Assignment Strategies 
 Control Plane Utilization 
 Benchmark 
 Orbit (Cluster Linking) 
 Tableflow 
 Tableflow Setup 
 Monitoring Tableflow 
 Iceberg REST Catalog 
 Integrate With Query Engines and External Catalogs 
 API Reference 
 Schema Registry 
 Setup 
 Enforce Schemas 
 Schema Linking 
 Manage Security 
 Reference 
 Billing 
 Audit Logs 
 Events 
 MCP Server 
 Accessing the Confluent Support Portal 
 Security and Privacy Considerations 
 Manage Console Access 
 Secrets Overview 
 API Reference 
 CLI Reference 
 Integrations 
 Dedicated Control Plane Cells and Release Windows 
 Control Plane Private Connectivity 
 Deprecation Policy 
 Powered by GitBook 
 On this page 
 For the complete documentation index, see llms.txt . This page is also available as Markdown .
 Ask 
 On this page 
 Kafka 
 Reference 
 Protocol and Feature Support
 The current implementation of the Apache Kafka protocol in WarpStream supports the basic ability to create topics, delete topics, produce data, consume data, and use consumer groups to load balance consumers and track offsets. Specifically, the following Apache Kafka messages are currently supported:
 Produce 
 InitProducerID 
 Fetch 
 ListOffsets 
 Metadata 
 OffsetCommit 
 OffsetFetch 
 FindCoordinator 
 JoinGroup 
 Heartbeat 
 SyncGroup 
 OffsetDelete 
 ApiVersions 
 CreateTopics 
 DeleteTopics 
 ListGroups 
 AlterConfigs 
 DescribeConfigs 
 DescribeCluster 
 DescribeGroups 
 DeleteGroup 
 LeaveGroup 
 CreateACLs 
 DescribeACLs 
 DeleteACLs 
 CreatePartitions 
 AddPartitionsToTxnResponse 
 AddOffsetsToTxnRequest 
 EndTxnRequest 
 TxnOffsetCommitRequest 
 DescribeTransactionsRequest 
 ListTransactionsRequest 
 The ListTransactions behaves like its Apache Kafka counterpart, but it accepts a special StateFilter value: EarliestOngoing that Apache Kafka does not accept. 
When EarliestOngoing is specified, other filters ( ProducerIDFilters , DurationFilterMillis , TransactionalIDPattern ) are not taken into account and WarpStream returns the transaction that has been created the earliest among all the transactions which are currently active.
 This can be useful to detect stuck transactions.
 GetTelemetrySubscriptions 
 PushTelemetry 
 ListConfigResources 
 We're continuously adding support for more Apache Kafka features and message types. Please contact us for specific feature requests or if you notice any discrepancies.
 Note that because of WarpStream's stateless architecture, many of the Apache Kafka protocol messages are irrelevant. For example, messages like:
 AlterReplicaLogDirs 
 ElectLeaders 
 ListPartitionReassignments 
 AlterPartitionReassignments 
 DescribeQuorum 
 UnregisterBroker 
 ControlledShutdown 
 StopReplica 
 LeaderAndIsr 
 have no meaning or value when using WarpStream because data durability and replication is managed by the underlying object store. Partitions do not have assigned "leaders", and clean shutdown is automated by virtue of the Agents being stateless.
 Transactions / Exactly Once Semantics 
 WarpStream supports Apache Kafka transactions and Exactly Once Semantics.
 To make use of it, please set enable.idempotence to true and add a non-empty transactional.id in your client configuration.
 Client Metrics (KIP-714) 
 WarpStream implements KIP-714 so connected Kafka clients can push their internal producer/consumer metrics to the cluster on a configurable schedule. See Client Metrics (KIP-714) for how to create subscriptions and view the data.
 Schema Registry 
 WarpStream has a BYOC Schema Registry built into the Agent binary. Check out the documentation for how it works.
 WarpStream BYOC Schema Registry supports most APIs listed in Confluent Schema Registry's API documentation . Here are the list of features it doesn't support:
 it doesn't support data contracts, so the metadata and ruleSet fields in the schemas are ignored.
 since metadata isn't supported, it doesn't support the /subjects/{subject}/metadata endpoint
 it doesn't support /mode endpoints.
 it doesn't support /exporters endpoints.
 it doesn't support subject aliases.
 it doesn't support compatibility groups
 Schema Validation 
 WarpStream supports server-side schema validation which not only validate that the record contains a valid schema ID, but that the record actually conforms to the corresponding schema.
 Currently, WarpStream supports two types of schema registries:
 Kafka-compatible Schema Registry
 AWS Glue Schema Registry
 It supports the following data formats: Avro, JSON Schema.
 For limitations and features not supported, check out the Enforce Schemas page.
 Record Retention Based on Custom Timestamps 
 Kafka implements record retention using the timestamps within the records themselves. If the client sets the timestamp using the CREATE_TIME timestamp type, it can send a record with a timestamp far in the future or the past. This will result in the record being deleted based on the timestamp rather than real-time passing.
 However, WarpStream differs in this aspect. In Warpstream, retention is based solely on the real-time when the record was created. Although you can set a custom timestamp for the record, it will not be used to calculate retention. The retention mechanism in Warpstream strictly adheres to the actual creation time of the record.
 Supported Clients 
 WarpStream should work with any correctly implemented Kafka client. Officially we support librdkafka , franz-go , as well as the standard Java client. Please check our documentation on tuning your clients for maximum performance with WarpStream.
 Known Incompatibilities 
 The current implementation any of the __tagged__ fields in the protocol and ignores them entirely.
 The current implementation does not enforce throttling and ignores all throttling-related fields/settings.
 All Kafka protocol requests have a maximum timeout of 15s (except for JoinGroup and SyncGroup).
 Previous Compression 
 Next Kafka vs WarpStream Configuration Reference 
 Last updated 1 month ago 
 Was this helpful?
 Privacy
 Cookie Settings 
 Transactions / Exactly Once Semantics 
 Client Metrics (KIP-714) 
 Schema Registry 
 Schema Validation 
 Record Retention Based on Custom Timestamps 
 Supported Clients 
 Known Incompatibilities 
 Was this helpful?
