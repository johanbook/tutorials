# MapReduce

**MapReduce** is a library for handling operations for large distributed
datasets. As the name might imply, it is based on two steps; a mapping and a
reduction.

The flow of the algorithm is as follows; the input data as handled by separate
worker nodes that perform the map operation and produce key-value pairs. These
are then shuffled such that similar keys are sent to the same reducer node. The
reducer nodes then reduce the incoming data and produce the finished result.

The algorithm is constructed to be fault-tolerant to network failure. However,
this assumes the map function is idempotent.

## Apache Spark

Spark is the successor to MapReduce, designed to mitigate some of its
shortcomings. For example, using filter and join operations in MapReduce is
awkward at best. It has better support for e.g. graphs, making it more fit for
machine learning.
