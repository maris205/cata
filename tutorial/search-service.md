# Search service

CATA search service is designed based on Minerva. It’s a a storage plugin of Drill that connects CATA decentralized storage and Drill's flexible query engine. CATA search support the standard SQL query.

CATA search service support the metadata search. For example, you could search the title, description, author of NFT or NFT collection. The image search will also be supported. That means you could directly post a NFT image and get the similar images.

Any data file stored on CATA can be easily accessed from Drill's query interface, just like a file stored on a local disk. Moreover, with Drill's capability of distributed execution, other instances who are also running Minerva can help accelerate the execution: the data stays where it was, and the queries go to the most suitable CATA nodes which stores the data locally and from there the operations can be performed most efficiently.
