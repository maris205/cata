# What is CATA

CATA provides a complete one-stop solution for Dapp data storage. CATA creatively extends the IPFS protocol to provide decentralized storage while achieving flexible metadata management, and is also compatible with SQL queries, providing extremely user-friendly and developer-friendly data access

## Background

Satoshi Nakamoto's revolutionary creation on the consensus protocol opened a new era of decentralized computing. People can freely contribute resources and obtain benefits in a fair and open network, and the decentralized ledger will honestly record all decisions made on the network without any privileged parties. The development of decentralized protocols looks similar to the early Internet protocols, but in essence they have achieved true decentralized autonomy, and a brand-new value delivery network at the upper level has also been born. However, the information era has developed for decades, and the actual production business has given birth to a large number of infrastructures, including database system, network protocol, file system, virtualization, etc. Also because of the infrastructure booms, Internet can support the upper-level application system.

The CATA technical team believes that the current decentralized network still has a long distance from real productization, and the scenarios that can be truly implemented today are extremely limited. The main reason for this is the lack of infrastructure. The throughput of the public blockchain has seen considerable development in the last few years, but the storage protocol is still at an early stage. Storage solutions in the traditional world often take into account both storage and retrieval, but the current mainstream decentralized storage (such as IPFS, Filecoin) is almost pure storage, which cannot meet the needs of data retrieval and content delivery. And some bandwidth-based data distribution projects (such as Meson Network) are also difficult to meet flexible query requirements.

## New infrastructure for decentralized data storage

Considering the current problems in decentralized storage, we believe that a complete storage system should not only have the capability of data persistence , but also provide highly data reading efficiency and flexible retrieval capability to meet all the storage requirements in the Dapp lifecycle.

We observed that at this stage, both traditional applications and decentralized applications still tend to delegate large-scale storage tasks to traditional centralized storage services. A simple centralized service architecture is shown in Figure 1.a in which the underlying file system supports the upper Big Data System(BDS), which in turn provides flexible and scalable storage capacity directly to the upper computation systems and applications. Unfortunately, while mature file systems are emerging in the decentralized world, there does not exist a mature and practical Big Data system, which is  exactly the role that CATA is expected to play, as shown in Figure 1.b.

![Figure 1 ](<../.gitbook/assets/image (6).png>)

Inspired by the distributed serverless query engine, CATA adopts a design scheme that decouples storage and retrieval functionality. The bottom layer is a persistent decentralized file storage network built through the IPFS protocol. The file system will completely get rid of centralized services (e.g. centralized metadata store module), and instead completely rely on P2P communication.It will split files at a specific granularity and use content addressing to locate data, ensuring data persistence and availability. At the same time, we creatively docked _Drill_, a distributed query engine, on top of the decentralized file system and built Minerva Layer.  In this way, the whole decentralized storage system will provide scalable storage functionalities functions for the upper Blockchain Systems and Dapps through Minerva Layer. Currently, we have already supported common data formats such as json, basic sql query capabilities and data export capabilities, and eliminate the centralized metadata store module.

## Why Drill

The evolution of modern big data systems has gone through roughly the following stages.

![Figure 2](<../.gitbook/assets/image (16).png>)

Here we have chosen Apache Drill as the base protocol and implemented the decentralized Minerva system on top of it because:

1. **Not just Hadoop**. Drill supports various distributed storage protocols, making it easier to scale to decentralized file systems
2. **No schema**.  Drill is free from the dependency on schema, which is a natural advantage for building decentralized systems, eliminating centralized schema and metadata store.
3. **No only SQL**. Drill supports nested data structures and has better scalability.
4. **Decentralized Topology**. Each node can be both leader and worker, which is suitable for decentralization concept.



## Competitor Comparison

|                                                                 | BigchainDB                            | Cassandra              | CATA                            |
| --------------------------------------------------------------- | ------------------------------------- | ---------------------- | ------------------------------- |
| Decentralization                                                | <p>Permissioned </p><p>Blockchain</p> | <p>Private</p><p> </p> | <p>Public </p><p>Blockchain</p> |
| Conensus                                                        | BFT                                   | None                   | POC+POA                         |
| Throughput                                                      | medium                                | high                   | medium                          |
| Latency                                                         | medium                                | Low                    | medium                          |
| <p>Capability of </p><p>structured data </p><p>processing</p>   | :white\_check\_mark:                  | ❌                      | :white\_check\_mark:            |
| <p>Capability of </p><p>unstructured data </p><p>processing</p> | :x:                                   | ❌                      | :white\_check\_mark:            |

