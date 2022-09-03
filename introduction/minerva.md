# Minerva

## What's Minerva?

Minerva is a data query engine built upon a combination of three co-operating components: Qri- the data management tool, Drill- the distributed query engine, and IPFS- the storage backend.

## System Structure

![](<../.gitbook/assets/image (4).png>)

Minerva takes advantages of the flexibility of Drill’s query engine and the scalability of IPFS’s decentralized filesystem. Each user of Minerva runs a local node, and the Minerva nodes form a peer-to-peer network. A user who has a particular dataset in her local store is a provider for that dataset, and can accept queries about it from other users in the network.

## How Minerva work?

![](<../.gitbook/assets/image (9).png>)

Figure 2 illustrates how datasets are stored on IPFS to work with Minerva. With Qri, a dataset is first sliced into a number of chunks and each chunk becomes an object on IPFS. These pieces of data construct a hierarchical tree structure, where all leaf nodes contain the data, and the others record hashes of lower-level nodes, like directories. Each of the intermediate nodes and the root node have its own content identifier (CID), i.e. the hash of the content, and the CIDs serve as the paths to a certain part of or the whole dataset on IPFS, respectively. Users can input standard SQL statements into Drill, specifying as the table name the IPFS path of the part of data they want to query. The query string will look like the following:

> SELECT ˋidˋ, ˋnameˋ FROM ipfs.ˋ/ipfs/QmRhDW...3SVi/employees.jsonˋ LIMIT 100

After parsing the SQL, Drill builds a distributed execution plan that will be sent to and executed on other nodes of Minerva who are serving the same dataset in the network.

Both decentralized read and write operations are enabled. Furthermore, Drill supports custom SQL functions, which are loaded from .jar files at runtime. Users can implement their conversion rules and analysis algorithms in the form of custom functions for a dataset, and distribute them with the dataset. Future users can benefit instantly by loading the custom functions from IPFS, in the same way as they specify a dataset stored on IPFS.

## Performance

![](<../.gitbook/assets/image (1).png>)

We have conducted preliminary performance evaluation on a prototype system in a 6-node cluster, each node running an instance of Minerva and IPFS working in private network mode. All statistics are averaged across 10 runs

Figure 3a shows how parallelization width affects query performance. The chunk size is fixed at 1MB. For both datasets, the plan time sees a slight increase when the queries are executed on more nodes parallely, while the execution time first decreases then increases. It makes sense that the planner would need more time to gather enough information about more providers capable of handling queries. The case for execution time can be explained as a mixed effect of two factors: when the queries are less distributed, the overall execution time mainly depends on the slowest node; when they are executed on more nodes, the overhead, e.g. increased network communication costs that build up system load, becomes prominent.

We compare the impact of different chunk sizes on the performance in Figure 3b. The max parallelization width is set to 3 in this experiment. The chunk size has a significant impact largely on the plan time, which is the time spent on finding which node is the most suitable to execute a specific fragment of the query. This is because the smaller the chunks are, the more of them a dataset must be divided into, therefore there are more units of data that the scheduler will have to consider.
