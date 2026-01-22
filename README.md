Distributed Analysis of Spotify Artist Networks
📌 Project Overview
This project implements a distributed big data pipeline to analyze the social structure of the Spotify Artist Collaboration Network. Using PySpark for scalable data ingestion and NetworkX for graph topology analysis, the project processes a dataset of 156,422 nodes and 300,386 edges  to determine how an artist's position in the network influences their popularity.

The pipeline culminates in machine learning workflows (Linear Regression and K-Means Clustering) to predict artist success and segment the network into community structures.

🛠 Technology Stack
Distributed Computing: PySpark (Spark SQL, MLlib)

Graph Analysis: NetworkX (Python)

Machine Learning: PySpark ML (Linear Regression, K-Means)

Visualization: Matplotlib

Environment: Google Colab / Cloud Storage



🚀 Key Features & Pipeline Architecture
1. Big Data Ingestion & Preprocessing

Ingestion: Utilized PySpark’s distributed reader to ingest large-scale CSV files (nodes.csv, edges.csv) with schema inference.

Data Cleaning: Implemented robust null handling:

Numerical columns (popularity, followers) imputed with 0 to preserve data integrity for aggregation.

Structural columns (spotify_id) dropped rows with nulls to ensure valid graph connectivity.


2. Network Topology & Graph Sampling

Challenge: Calculating complex metrics (e.g., Betweenness Centrality) on 150k+ nodes is computationally expensive.


Solution (BFS Sampling): Instead of random sampling (which destroys community structure), implemented Breadth-First Search (BFS) traversal to create a representative subgraph of 1,000 nodes.


Validation: Verified the sample's validity by comparing its degree distribution to the full graph, confirming both followed a Power Law distribution.


3. Centrality Measures & Analysis
Calculated five key centrality measures to identify network "influencers":

Degree Centrality: Connection volume.

Betweenness Centrality: Identification of "bridge" artists connecting genres.


PageRank: Algorithmic ranking of artist influence.



4. Machine Learning & Predictive Modeling
Linear Regression (Predicting Popularity):

Features: Followers + Centrality Measures.

Result: Identification that Betweenness Centrality is a significant predictor of popularity, highlighting the importance of being a "bridge" in the music industry.




K-Means Clustering (User Segmentation):

Standardized features to handle scale disparity (e.g., Millions of followers vs. 0.002 PageRank).

Evaluated K=2 to K=10; determined K=2 as optimal with a Silhouette Score of 0.9988.


Insight: The network is sharply divided into "Superstars" (hub nodes) and the "General Population".




📊 Key Findings

Network Structure: The graph is extremely sparse (Edge Density: 0.002) with a small diameter (2), indicating a "star-shaped" topology centered around massive hubs.



The "Bach" Effect: Johann Sebastian Bach was identified as the central hub (Rank #1 in all centrality measures), connecting the entire subgraph.


Power Law: The analysis confirmed the music industry follows a strict power law distribution where a minute fraction of artists hold the majority of influence.
