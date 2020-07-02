# Network-analysis-of-CitiBike-data-with-K-Means-Clustering-and-DBSCAN

This reporsitory examines the CitiBike data using network science methods and clustering techniques.
The datais available at https://www.citibikenyc.com/system-data and 
the trip history data is available at https://s3.amazonaws.com/tripdata/index.html (JC-201910-citibike-tripdata.csv.zip Nov 5th 2019, 05:10:56 pm was used in this experiement).
The bike station network is further analysed using K-means clustering and DBSCAN.

The file consisted of the following attributes -
Trip Duration (seconds), Start Time and Date, Stop Time and Date, Start Station, Name,
End Station Name, Station ID, Station Lat/Long, Bike ID, User Type (Customer = 24-hour
pass or 3-day pass user; Subscriber = Annual Member), Gender (Zero=unknown; 1=male;
2=female), Year of Birth.

In order to visualise the network, the following data processing is conducted.
• The csv file is stored into a pandas dataframe and 50 entries are randomly sampled.
• From the combined list of start and end station ids in the sampled data, all the unique
start and end station ids with their corresponding station name, latitude and longitude
are extracted into a new data frame. Duplicate values are removed.

Each unique station id forms a distinct node in the network. The nodes are plotted on
the network based on the station latitude and longitude values.
• The edges of the network are created using all the start and end station id pairs in the
sampled set.
• NetworkX is then used to plot a directed graph with the above set of nodes and edges.

The resulting graph has 47 edges and 35 nodes (stations). Majority of the nodes are in
a dense cluster with some nodes sparsely located as outliers.

The following properties of the dataset are noted –
• Degree distribution: The degree centrality for a node is defined as the fraction of nodes
it is connected to. In the sampled dataset, node 3186 (Grove St PATH) was found to
have the the highest paths connected to it. Since it’s a directed network, the in-degree
and out-degree centrality of all the nodes is also computed.
• Centrality measures: Closeness centrality of a node n is the reciprocal of the sum of the
shortest path distances from n to all the other (n-1) nodes. Higher values of closeness
indicate higher centrality. So, as expected, node 3186 has highest value of closeness
and betweenness centrality.
• Clustering: A clustering coefficient is a measure of the degree to which nodes in a graph
tend to cluster together. The average clustering coefficient for this network is computed
to 0.061.
• PageRank: PageRank measures the importance of each node in a graph in terms of the
number of incoming edges linked to it. As expected, node 3186 has the highest value
of page rank.
• HITS: Return HITS hubs and authorities values for nodes.
• Path length: The shortest paths are computed using all nodes as source nodes.
• Connectivity: The graph has 2 weakly connected components and 25 strongly
connected components.


