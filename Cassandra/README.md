## Cassandra:

- Cassandra is a leader less multi node distributed database.
- Node communicate with each other with gossip protocol.
- Data is divided in Cassandra in form of partition.
- Every node is assigned a partition token.
- Replication factor 3 is standard in Cassandra, Which provide consistency, availability and performance.
- Replication factor 3 means any write will store to 3 nodes
- Quorum for consistency level , Quorum means reached to majority of note in case on 3 nodes Quorum means if write done to 2 nodes acknowledgement will be sent
- Question come if let's say one node is stale for some reason cassandra will repair the node(read repair) and make sure current data will be sent back to client
- Request land to Coordinator node , then coordinator node check which partition data belongs to and send the request to that node to get the data , in case the node does not respond in time the replication node will respond.
- Coordinator node is responsible for snitches which mean it is responsible to find node with minimum latency.
- If coordinator node get a read request , coordinator will check which partition the data belongs to and send the request to all replication nodes , if two nodes send the data with two different timestamp cassendra ask the node with less timestamp to read repair.
- Cassandra uses flush operation to flush data from in-memory called memtable to disk called SSTable (Sorted string table) .
- Once data write completed to commit log and memtable , cassandra send write acknowledgement back to client.

### Reference:
- https://www.youtube.com/watch?v=YjYWsN1vek8
- https://www.youtube.com/watch?v=JEwkI0W-wAk
- https://medium.com/@sevanthi404rt/behind-the-scenes-of-cassandras-write-path-4690b7ec11b2
