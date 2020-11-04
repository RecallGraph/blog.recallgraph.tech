## Never lose your old data again

Have you ever wished you had access to a specific past version of some (possibly deleted) record (address/insurance policy/claim, etc)? If your answer is 'yes', then the following anecdote might ring a bell (or twenty):

*"In June, 1997, Hudson Foods had to recall 25 million pounds of beef in an attempt to stem an outbreak of E. coli, at that time the largest recall of food in the United States. Back then, the product that was recalled was valued at $25 million – around one fifth of Hudson’s annual production. Hudson knew that only a much smaller portion of the beef needed to be recalled based on a specific supplier. However, because their database only supported a current version of the data – which beef came from which sources today – and didn’t show a view of the data as it existed on the day the processing occurred several weeks prior – the entire product set had to be recalled. In short, the absence of an appropriate time-varying database cost Hudson Foods 20% of their annual production."*

(Source: [Temporal Databases: Why you should care and how to get started (Part 1 of 3) - Data Science Central](https://www.datasciencecentral.com/profiles/blogs/temporal-databases-why-you-should-care-and-how-to-get-started))

%[https://recallgraph.tech/]
 
[RecallGraph](https://recallgraph.tech/) solves the above, and other similar predicaments by forever keeping a record of all the changes your data may have undergone. It even lets you travel back and forth in time to get a view of your data as it was at a specific point in time. **With RecallGraph, you’ll never lose your old data because it can store and access older revisions of all your data in an instant**.

> RecallGraph is a good fit for a wide variety of business needs for tech users across multiple disciplines.

# Highlights
1. Free and open source.
1. **Never lose your old data**. RecallGraph can store and access older revisions of all your data in an instant.
1. Run **graph traversals on historic data** as easily as on current data.
1. **REST API** - No need to learn yet another query language to access temporal superpowers. **Call the API from anywhere**, including servers and browsers.
1. Recoverable Deletes, Purge, Import and more - Any data that you delete can always be restored, unless its history is explicitly purged from the database. You can also **import your existing non-temporal data** and begin tracking revisions from there.
1. ACID Transactions - All write operations are wrapped in ACID-compliant transactions, so your data is always consistent.
1. Distributed Tracing Support - RecallGraph is an [OpenTracing](http://opentracing.io/)-compliant service. Plug into your existing distributed tracing infrastructure and get insights and performance metrics OOTB.

> If your organization generates data, it also mutates it. You should start thinking about persisting historic versions NOW!

# Target Audience
Developers, DBAs and data analysts who have a need for retention of historic data. This could be a requirement in almost every business domain since audit trails are universally applicable. Besides this, social networks, e-commerce platforms, CMSs, MDM systems, data pipelines all have a recurring need for storing and accessing old revisions of data for several use cases. **RecallGraph is a good fit for a wide variety of business needs for tech users across multiple disciplines**.

# Must-have scenarios
1. Audit trails are a regulatory mandate for companies beyond a certain size in most jurisdictions. With a temporal database, **audit trails are built-in, always available and always current**.
1. Data versioning is hard - **really, really hard**. One attempt at monkey-patching a versioning layer on top of an existing database schema is enough to convince most (sane) developers on this point.
1. **If your organization generates data, it also mutates it**. You should start thinking about persisting historic versions NOW, rather than as an afterthought or when a particular historic analysis or report is required (and you've already clobbered over the old data).
1. Binlogs ≠ (Streamlined, queryable history across the entire change history of the database). Let's not even go there.

> Like git, but for data.

# Why RecallGraph
1. RecallGraph runs on top of **ArangoDB**, [currently the No. 1 graph database on G2 by CSAT scores](https://www.g2.com/categories/graph-databases?utf8=%E2%9C%93&order=top_shelf) . It truly stands on the shoulders of giants.
1. Very easy and well-documented installation, guides and tutorials (both for [ArangoDB](https://www.arangodb.com/docs/3.6/) and [RecallGraph](https://docs.recallgraph.tech/)).
1. **In-depth instrumentation** using the OpenTracing standard.
1. Actively maintained and <24 hr TAT on all [support requests](https://gitter.im/RecallGraph/community).

# Impact
1. Happy devs, ops, DBAs, analysts, auditors, management.
1. Unprecedented customer support, backed by customer records (any version) and referential transaction logs **going all the way back to the beginning of time**.
1. **Like git, but for data** -> minimal cognitive overhead, leading to rapid and painless adoption across the org.
1. Migrate your existing data and start versioning from that point onward.

> Most temporal graph database designs/implementations exist only in research papers. Only a handful of mainstream, production-ready implementations have been built till date.

# Feature Roadmap
RecallGraph is built on the [open core](https://en.wikipedia.org/wiki/Open-core_model) model, meaning it has a core feature set that is, and will remain forever, free and open source. There will soon be premium features built on top of this core foundation. Below is a sneak preview into the exciting features that are planned for future releases. **Note:** Some of these may sit behind a paywall.

1. **Full bi-temporality** (support for a *"valid time"* dimension in addition to *"transaction time"* already present in the open-source offering.
1. **Parallel realities** - similar to branching in source version control, your data's history will be able to branch out into multiple timelines. This could be used for scenarios like 'what-if' analysis and direct testing on production infra with non-production data.
1. **CQRS/ES operation mode** - instead of sending entity contents for creates/updates, you can send the events and corresponding deltas that constitute the write event. These can be batched or async-queued for faster response times. See https://docs.microsoft.com/en-us/azure/architecture/patterns/cqrs for more information on the CQRS pattern.
1. **Multi-shard cluster support** - RecallGraph uses ACID transactions for its internal writes. At present, a limitation of ArangoDB (the underlying DB engine on which RecallGraph runs) is that it does not support ACID transactions for writes that are distributed across multiple primaries. A future premium version of RecallGraph will address this using a custom transaction manager.
1. **Complex Event Processing** - Since RecallGraph is first and foremost a rich store of events representing a complete historical log of all changes to a database, it stands to reason that CEP be offered as a built-in feature for those who need to perform temporal analyses.
1. **Multiple temporal query classes** - Other than point-in-time queries, there are other classes of temporal queries (including time-interval, time-respecting traversals and more). Future versions of RecallGraph will include support for these query classes. See this [YouTube video](https://www.youtube.com/watch?v=A953O3hT1Os) to learn more.

> For a special offer featuring LIFETIME ACCESS to all future premium features, check out [this deal](https://appsumo.com/recallgraph/) on the AppSumo Marketplace!

# Behind the Scenes
## Inception
I started building RecallGraph in Jan 2019, the inspiration for which came from two distinct sources: Prior to RecallGraph, I got the chance to work with graph databases and event stores in two independent projects. Somewhere along the way, it struck me that one could combine the core concepts of both into a single product.

In fact, in most projects I had worked on, there was always an underlying problem around data history retention that I felt could be best addressed directly in the DB layer. This is what put me on the path to building RecallGraph.

## Fun fact
I had initially thought this would be a simple hobby project that would take no more than a couple of weeks to build. It is now almost 2 years in the making, and there's still a long list of exciting new features to build. It took me a while to realize the sheer magnitude and complexity of the problem I had picked to tackle. **Most temporal graph database designs/implementations exist only in research papers. Only a handful of mainstream, production-ready implementations have been built till date.**

# Appendix - Special Offer

%[https://appsumo.com/recallgraph/]

RecallGraph is now listed on the [AppSumo Marketplace](https://appsumo.com/recallgraph/)! This deal, priced at just $29, gives you the following:
1. **LIFETIME ACCESS** to all future premium features that RecallGraph will ever release.
1. A **1 hour consultation call** with me (normally priced at $59) to help you dive deeper into concepts, use cases, and how RecallGraph can address your temporal data management needs.

This deal is available exclusively through the AppSumo Marketplace. So go ahead and [grab your AppSumo Code](https://appsumo.com/recallgraph/) now!