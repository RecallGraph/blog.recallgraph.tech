---
title: "A Successor Project: Minigraf"
datePublished: 2026-04-25T18:45:43.406Z
cuid: cmoeowkto004928jp6b5b0btc
slug: a-successor-project-minigraf

---

It has been five years since the last RecallGraph release. The repository is now formally archived, the docs site remains online for reference, and this blog will not see new posts after this one. None of that is news to anyone who has been following along; the project went quiet long before it went archived.

What is worth saying, briefly, is that the underlying problem RecallGraph was built to address has not gone away — and that there is now a successor project worth pointing to.

#### Minigraf

[Minigraf](https://github.com/project-minigraf/minigraf) is an embedded, single-file, bi-temporal graph database written in Rust, with Datalog as its query language. It is the second attempt at the same fundamental thesis: that point-in-time queries over evolving graph data are a first-class need rather than a bolt-on.

The differences from RecallGraph are not subtle:

*   **No host database.** RecallGraph required ArangoDB plus a Foxx microservice deployment. Minigraf is a single library you embed, with one `.graph` file as the storage. `cargo add minigraf`, open a file, query.
    
*   **Bi-temporal as a primitive.** RecallGraph handled transaction time well and treated valid time as a future feature. Minigraf supports both from day one — the dimension along which a fact was *recorded* and the dimension along which it was *true* in the world.
    
*   **Datalog, not REST.** Recursive rules, multi-hop traversals, and time-travel as just another relation rather than a separate API surface.
    
*   **Runs anywhere Rust runs.** Including WebAssembly, Android via Kotlin bindings, and iOS via Swift bindings. The deployment surface is the inverse of RecallGraph's.
    

#### Why Now

The audience for this kind of database has shifted. In 2019, the people who cared about versioned graph data were primarily working on audit trails, regulatory compliance, and historical analysis. Those use cases are still real, but the loudest current demand is from people building agent-shaped systems — programs that maintain beliefs, revise them, and need to be able to explain themselves later. Bi-temporal databases turn out to be a remarkably good fit for this, in ways that were not at the front of my mind when I first designed RecallGraph.

A working sibling project, [temporal-reasoning](https://github.com/adityamukho/temporal_reasoning), uses Minigraf as the storage layer for a structured-memory skill aimed at coding agents. It is the most concrete validation of the agent-memory use case so far.

#### If You Subscribed for Updates

The RecallGraph repository, docs, and this blog will remain available as a reference. Active development and new writing on temporal databases will move to [adityamukho.com](http://adityamukho.com) and the [Minigraf repository](https://github.com/project-minigraf/minigraf). A longer retrospective on what changed in my thinking between the two projects is [here](https://adityamukho.com/minigraf-a-spiritual-successor-to-recallgraph).

If you have been running RecallGraph in production and want to talk about a migration path, get in touch through the Minigraf repo.

Thanks for reading along — see you on the other side.