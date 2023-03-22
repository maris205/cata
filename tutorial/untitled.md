# Getting Started

CATA network contains two parts:

1 metadata storage, which is designed based on Minerva.

2 file storage, which is designed based on FLOW resource  node in first period.

Minerva is a storage plugin of Drill that connects IPFS's decentralized storage and Drill's flexible query engine.  We then revise the IPFS to Flow. Any data file stored on FLOW  can be easily accessed from Drill's query interface, just like a file stored on a local disk. Moreover, with Drill's capability of distributed execution, other instances who are also running Minerva can help accelerate the execution: the data stays where it was, and the queries go to the most suitable nodes which stores the data locally and from there the operations can be performed most efficiently.

FLOW resource storage Cluster is a distributed application that works as a sidecar to FLOW peers, maintaining a global cluster pinset and intelligently allocating its items to the IPFS peers: FLOW Cluster provides data orchestration across a swarm of FLOW daemons by allocating, replicating and tracking a global pinset distributed among multiple peers.
