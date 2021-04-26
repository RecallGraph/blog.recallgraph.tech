## Temporal Query Types

At the time of writing this post, all of RecallGraph's API endpoints are designed to serve a particular type of temporal query, viz. _point-in-time_ queries.

However, there are actually several classes of temporal queries that a temporal database could potentially support. Some of them may be achieved on RecallGraph, albeit by clever usage of parameter combinations on certain general purpose endpoints.

# Temporal Query Classes
## Point-in-Time
This is what most people will already be familiar with. Running a point-in-time query effectively amounts to asking a question on a historic snapshot of the data. Your data has a certain state at any given time, which gets modified through write-actions performed on it from time to time.

If you could rewind the clock and get back the state of the data as it was at a particular time in the past, you could then run queries on that state as if it were the present. This is exactly what a point-in-time query does.

## Time Interval
Extending the analogy of rewinding the clock in the section above, imagine replaying the events from a specific historic time point, up to another time point relatively in the future (this could be another historic time point, the present or even a time in the future). During the replay, you gather certain data points of interest as you travel along the timeline. Once you're done traversing the time interval, you report back the data points that have been collected.

This could be used, for example, to identify all objects that were alive during the interval (the entire interval or a portion of it). These could additionally be also required to satisfied a bunch of provided filter criteria.

## Time-Point Lookup
This is the converse of the point-in-time query. Here, given certain objects and a bunch of filter criteria, we ask the database to search through the entire timeline for a point (or points) where the given objects had states that satisfied the filter criteria.

For example, this could be used to find the most recent time when the prices of all flight tickets between two cities were below a certain threshold.

## Time-Interval Lookup
Extending the time-point-lookup concept described above, this query asks for an interval (or all intervals) where the object states matched the provided filter criteria.

For example, we could use this to find the largest interval during which all objects matching a filter criteria were alive through the interval.

# Appendix: Temporal Traversals and Analysis
All the query classes described above pertain to individual document states, and hence are largely agnostic to the database's underlying model (KV/Document/Relational/Graph).

In the context of graph traversals specifically, there are a number of additional temporal query types that can be defined, specifically pertaining to traversing temporal graphs or networks. This is a large field of study with research on the state-of-art still ongoing, esp. on temporal network analysis.

Many definitions are still being drafted and revised, but a few patterns seem to have emerged already. These are briefly explored in the following Wikipedia article - https://en.wikipedia.org/wiki/Temporal_network.


