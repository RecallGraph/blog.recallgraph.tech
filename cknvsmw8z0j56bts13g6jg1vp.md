## Time-Series vs Temporal Databases

Another question I often get:

> "How does RecallGraph stack up against AWS Timestream (or some other time-series database)"?

# Short Answer
RecallGraph is **NOT** a time-series database, and hence should not be compared to one. Rather, it is a **temporal** database, and is best thought of as a graph database with a built-in version-control layer for its data.

# Long Answer
AWS Timestream (and other time-series databases) and RecallGraph (and other temporal databases) both deal in timestamped events as their primary data unit. Due to this, there is in fact some overlap between their capabilities. The difference lies in what semantic representations they primarily use these events for. Each is therefore optimized to perform better in its own focus area, and each offers differentiating features that the other does not.

Most time-series databases are optimized for high volume ingestion of multiple event streams, where each event usually represents a single reading or measurement from an IoT device or some system usage/performance metric. On top of this, they provide multiple aggregation, statistical and down-sampling capabilities, and are best used for monitoring a set of time-varying metrics or measurements, acting as a data source for dynamic visualizations of these metrics, setting alerts/thresholds and aggregating/summarizing over a huge number of events in a stream or in a time window.

A temporal database, on the other hand, uses events as markers that record a history of changes to an entity (document) over time. In this context, an event is analogous to a commit in a version control system like Git. Temporal databases can therefore time-travel over the history of a document, a collection or the entire database, letting users see the state of their data as it was at some time in the past (or future!). Temporal databases are therefore optimized for resiliency and referential integrity across linked entity histories, rather than being tuned to drink from a fire hose of loosely related events.

Temporal databases can be relational, document, key/value or graph databases at heart (RecallGraph is multi-model - KV + Document + Graph). Temporal databases often support multiple time dimensions, each with it own semantic significance (see https://en.wikipedia.org/wiki/Temporal_database).

One area where the capabilities of both time series and temporal databases can potentially overlap is _Complex Event Processing_, since both types of databases are event stores at heart, and can each choose to offer their respective flavors of CEP.