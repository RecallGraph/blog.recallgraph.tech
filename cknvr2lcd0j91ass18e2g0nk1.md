## Does RecallGraph Support Schema Versioning?

A question I've been asked more than once on ArangoDB's community forums and elsewhere:

> "Is RecallGraph supposed to be used for versioning document schemas?"

The answer depends on what you provision the service for:

1. If you've deployed an RG instance with the primary purpose of versioning and serving metadata for your application's data, then you can just as well use it to store (and version) JSON-based schema documents. There has to be an application-specific mechanism to link a document (or its revision) to a particular schema version.

1. If, on the other hand, you use RG as the primary storage and query backend for your application data, you have to manage schema versions yourself, since RG itself is agnostic to the structure of the data you put in it. You might solve for this by using a separate schema-versioning tool like [ArangoMiGO](https://github.com/deusdat/arangomigo), or using a hybrid approach wherein RG stores (and versions) both your metadata as well as the actual business data.