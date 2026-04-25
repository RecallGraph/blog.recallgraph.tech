---
title: "Will RecallGraph Support My Favorite Graph Query Language?"
datePublished: 2021-04-24T13:22:21.395Z
cuid: cknvrve6l0jddass1h3vefun0
slug: will-recallgraph-support-my-favorite-graph-query-language
tags: graphql, graph-database

---

If the query language in question supports arbitrary traversal depths and temporal clauses, then it could, hypothetically, be used to query RecallGraph's data.

However, the latter requirement rules out most popular graph query languages, including GraphQL, Gremlin, AQL and Cypher.

It may be possible to support TSQL (with recursive CTE's). One notable query language that has the required features is Datalog, and it has been used successfully in other (bi-)temporal graph database offerings.

It should be noted, however, that these options are merely in the realm of possibility at the time of this writing. None of these languages are planned to be supported in the current roadmap, although they may be considered in the future.