# Cloud based Object Storage System

- Data (set of objects) is partitioned and stored using consistent hashing on a ring topology of 264 id space. Number of nodes (Containers/VMs) = 3 and each representing 500 virtual nodes.
- Each object is replicated in N nodes (N is configurable). Consistency among replicas is achieved by using vector clocks, read-write quorums, and rea-repair and anti-entropy process. [Dynamo Paper](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)
- Every t seconds (t is configurable), system check for hotspots and migrate VM/container using volume-to-size ratio.
- REST API for user to be able to create/delete objects.
- The API returns the following in a JSON object: Success or failure, Vector clocks of all replicas, Node number where the write took place (in case of write)
