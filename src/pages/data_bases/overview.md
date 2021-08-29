# Databases

A database is a service dedicated to storing and retrieving data. A database
typically has the following attributes

- **Persistence** Data is persisted through program failures.
- **Concurrency** Support many concurrent read and writes.

which are requirements in many production environments that need to story any
form of data (such as user accounts).

Databases are usually divided into relational and non-relational databases.

## Relational Databases

A relational database imposes a relational structure on its data. This structure
is described in schemas. Most relational databases support Structured Query
Language (SQL).

### ACID

A good relational database should have the ACID attributes as stated below.

- **Atomicity**. A transaction involving several entities fail all or succeed
  all.
- **Consistency**. Database is updated directly after a transaction. If there is
  an error in a transaction, the database will be rolled back. This is in
  contrast to eventual consistency where a database will update at some after
  the transaction, but not necessarily directly.
- **Isolation**. Although queries are run in parallel they behave as if serial.
- **Durability**. Changes to the database are permanent.

### Indexes

One can index a specific column for faster search speeds in exchange for slower
writes and more memory consumption. It is useful for e.g caching.

## Non-relational Databases

A non-relational database (often referred to as NoSQL) is database that does not
require relational data. NoSQL is suitable for heterogeneous data where this no
natural relations (such as random documents).

### Key-Value Storage

A key-value storage is a database that store values by keys. This is suitable
for cache or system configurations (used in e.g. `etcd`).

### Blob store

Blob (binary large object) is unstructured data, in contrast to JSON. Does not
fit into a SQL database. As of writing this, Google Cloud Storage and Amazon S3
offers this. Usually behaves like a key-value store.

## Other Types

Some other specialized data bases are:

- **Time series database** Handles time-series data. Often used for monitoring.
- **Graph database** Uses a graph model.
- **Spatial database** For storing spatial data, such as points on a map.

## Deployment

### Shards

The data of a database server can be divided into different shards which can be
shared across several different databases.
