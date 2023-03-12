# Getting Started

CATA network contains two parts:

1 metadata storage, which is designed based on Minerva.

2 file storage, which is designed based on IPFS cluster in first period.

Minerva is a storage plugin of Drill that connects IPFS's decentralized storage and Drill's flexible query engine. Any data file stored on IPFS can be easily accessed from Drill's query interface, just like a file stored on a local disk. Moreover, with Drill's capability of distributed execution, other instances who are also running Minerva can help accelerate the execution: the data stays where it was, and the queries go to the most suitable nodes which stores the data locally and from there the operations can be performed most efficiently.

IPFS Cluster is a distributed application that works as a sidecar to IPFS peers, maintaining a global cluster pinset and intelligently allocating its items to the IPFS peers: IPFS Cluster provides data orchestration across a swarm of IPFS daemons by allocating, replicating and tracking a global pinset distributed among multiple peers.

