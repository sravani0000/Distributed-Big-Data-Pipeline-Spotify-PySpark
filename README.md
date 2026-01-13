Overview
Architected a distributed data ingestion and processing pipeline to analyze a large-scale social graph of Spotify artist collaborations. The project focused on handling high-volume data ingestion into a Spark environment, ensuring partition efficiency, and performing complex graph-based transformations.

Technical Stack:
Processing Engine: Apache Spark (PySpark)

Data Structure: Distributed Property Graphs (Nodes/Edges)

Library: Spark MLlib, NetworkX

Cloud Logic: Designed for scalable ingestion from Cloud Storage (S3/GCS buckets)

Cloud Engineering Highlights:

1. Distributed Ingestion: Configured PySpark to ingest and infer schemas for datasets exceeding 300,000 collaboration records, ensuring data integrity across distributed partitions.

2. Partition Optimization: Implemented efficient data partitioning strategies to handle the "Johann Sebastian Bach" hub-node bottleneck, optimizing shuffle operations during graph traversal.

3. ETL Pipeline: Developed a transformation layer that cleaned raw metadata and converted categorical artist features into standardized vectors for K-Means clustering.

4. Scalability Analysis: Validated system performance using Silhouette Scores and PageRank, proving the pipeline's ability to segment the "superstar" outliers from the general artist population at scale.
