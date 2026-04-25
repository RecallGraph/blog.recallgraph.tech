---
title: "Does RecallGraph Support Transactions?"
datePublished: 2021-04-26T05:34:44.627Z
cuid: ckny61qs90cdiews18lrq1a42
slug: does-recallgraph-support-transactions
tags: graph-database

---

# Quick reference
- For single document writes (create/update/replace/delete) - **YES**.
- For bulk document writes (create/update/replace/delete) - **NO**.
- For restoring a _node-brace_ path pattern resolving to a single document - **YES**.
- For all other restores - **NO**.
- For purge (any path pattern) - 
    - All service-collection entries are removed in a single transaction. If the number of documents being purged is large, this may be automatically split into multiple smaller transactions.
    - If user-objects are also to be deleted, these are deleted in per-collection transactions.

# A brief explanation on the above limitations
Although RecallGraph supports bulk updates, it wraps each individual update in its own separate transaction. This is because each update involves a bunch of associated event log entries and skeleton graph updates, snapshot insertions, etc. On an average, around 5 internal documents are created/updated during a single node update, although in some cases this number could go higher.

Since ArangoDB does not support nested transactions, it is not possible to wrap these individual small transactions under a larger envelope transaction. It might be useful to support bulk updates in a single transaction in future versions of RecallGraph, but it would need some careful design in order to avoid overshooting memory limits. Here's a list of limitations that must be accounted for when using the RocksDB engine - https://www.arangodb.com/docs/stable/transactions-limitations.html#rocksdb-storage-engine.

Supporting bulk updates in a single transaction is thus not a straightforward matter.