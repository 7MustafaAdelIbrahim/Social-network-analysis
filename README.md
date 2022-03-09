# Social-network-analysis
     A key technique in modern sociology to investigate social structures through networks and graph theory.


From ***online social networks such as Facebook and Twitter to transportation networks such as bike sharing systems*** , networks are everywhere and knowing how to analyze them will open up a new world of possibilities for you as a data scientist.

This repo will equip you with the skills to analyze, visualize, and make sense of networks. and developing your network thinking skills and be able to look at your data with a fresh perspective.

We'll build on our knowledge and skills to tackle more advanced problems in network analytics, and gain the conceptual and practical skills to analyze evolving time series of networks, learn about bipartite graphs, and how to use bipartite graphs in product recommendation systems.
We'll also take about graph projections, why they're so useful in Data Science, and figure out the best ways to store and load graph data from files. 


Networks!
the intersection of biological network science and infectious disease
Let me first ask you a question: 
             what are some examples of networks? 
In a social network, we are modeling the relationships between people. 
In a transportation network, we are modeling the connectivity between locations, as determined by roads or flight paths connecting them. At its core, networks are a useful tool for modeling relationships between entities.

By modeling your data as a network, you can end up with:
gaining insight into what entities (or nodes) are important, such as broadcasters or influencers in a social network.
Additionally, you can start to think about optimizing transportation between cities.
Finally, you can leverage the network structure to find communities in the network. Let's go a bit more technical. 

## Network Structure
Networks are described by two sets of items: nodes and edges. Together, these form a "network", otherwise known in mathematical terms as a "graph".
Nodes and edges can have metadata associated with them.

![image](https://user-images.githubusercontent.com/84151016/157509985-077a0c77-1654-4ace-83ff-a78362e31a45.png)


For example, let's say there are two friends, Hugo and Eric, who met on the 21st of May, 2016. 

![image](https://user-images.githubusercontent.com/84151016/157510096-8086ce4f-5b4e-476b-ae52-33d54c7c1325.png)

In this case, the nodes may be "Hugo" and Eric", with metadata stored in a key-value pair as "id" and "age".
The friendship is represented as a line between the two nodes, and may have metadata such as "date", which represents the date on which we first met. In the Python world, 

### NetworkX API Basics
There’s a library called NetworkX that allows us to manipulate, analyze and model graph data.
Let's see how we can use the NetworkX API to analyze graph data in memory.

we can initialize an empty graph to which we can add nodes and edges.
I can add in the integers 1, 2, and 3 as nodes, using the add_nodes_from method, passing in the list [1, 2, 3] as an argument.
The Graph object G has a dot-nodes method that allows us to see what nodes are present in the graph, and returns a list of nodes. If we add an edge between the nodes 1 and 2, we can then use the G-dot-edges method to return a list of tuples which represent the edges, in which each tuple shows the nodes that are present on that edge. 


## Types of graphs. 

#### Undirected graphs

Undirected graphs are named as such because they are comprised of edges that don't have any inherent directionality associated with them.

![image](https://user-images.githubusercontent.com/84151016/157510611-7997fef5-399c-4a38-b293-737eee328c21.png)


For example, there are social graphs like Facebook. As when one user befriends another, the two are automatically connected with an edge.
This is commonly drawn as a line with no arrows between two circles.

### Directed graphs
There is an inherent directionality associated with the graph.

![image](https://user-images.githubusercontent.com/84151016/157510673-ac61cf3f-1cf4-4d89-833d-b71f0bfe0f50.png)


Twitter's social graph is a directed network.
This is because of the nature of how users interact with one another. For example, one user may follow another, but that other user may not follow back.

### Multi-edge (Directed) graphs

![image](https://user-images.githubusercontent.com/84151016/157510771-6f2d8106-9a71-4ab5-be3f-5c78d61602b3.png)


For example, we may want to model trips between bike sharing stations. Each trip may be one edge between the pair of stations.

 
we can likewise instantiate a MultiGraph using nx-dot-MultiGraph. If we check for its type, it will be of the MultiGraph class. Likewise for the MultiDiGraph object. Sometimes, for practical reasons, it may be too memory-intensive to model multiple edges per pair of nodes, and so one may choose 


### Weights on graphs
to collapse the edges into a single edge that contains a metadata summary of the original.
For example, we may want to collapse these three edges into a single one and give them a "weight" metadata 
with the value "3", indicating that it was originally 3 edges between the pair of nodes. Let's go through one final concept: the idea of 

![image](https://user-images.githubusercontent.com/84151016/157511004-e24d3aac-f447-42c7-a17e-5572cecf3ffc.png)


### Self-loops

Nodes that are connected to themselves

![image](https://user-images.githubusercontent.com/84151016/157511095-3b20eee5-2ea6-40e4-9a1c-14b6b5c2f983.png)

Self-loops can be used in certain scenarios, such as in bike sharing data, where a trip begins at a station and end at the same station. One of the exercises you will encounter will leverage what you've learned so far about the NetworkX API to find edges that are self-loops in a graph. 


## Network visualization
          A node-link diagrams involving more than a hundred thousand nodes. 
### Irrational vs. Rational visualizations

![image](https://user-images.githubusercontent.com/84151016/157511561-dad39835-24a8-46a7-b654-dd9f327d4c7c.png)


They purport to show a visual representation of the network, but in reality just show a hairball.
In this section, we are going to look at alternate ways of visualizing network data that are much more rational. 

### Matrix plot

![image](https://user-images.githubusercontent.com/84151016/157511613-3f800641-93aa-4190-9487-b48b706d2f47.png)


In a Matrix Plot, nodes are the rows and columns of a matrix, and cells are filled in according to whether an edge exists between the pairs of nodes. On these slides, the left matrix is the matrix plot of the graph on the right.

#### In an undirected graph. 

![image](https://user-images.githubusercontent.com/84151016/157511853-120b8959-d891-4283-87aa-ce5b9b39bc7c.png)

The matrix is symmetrical around the diagonal, which I've highlighted in gray. I've also highlighted 
one edge in the toy graph, edge (A, B), which is equivalent to the edge (B, A).Likewise for edge (A, C), 
it is equivalent to the edge (C, A), because there's no directionality associated with it. 

#### Directed matrices

![image](https://user-images.githubusercontent.com/84151016/157511979-4150c688-f685-4491-be1d-33e119c644d2.png)

If the graph were a directed graph, then the matrix representation is not necessarily going to be symmetrical. In this example, we have a bidirectional edge between A and C, but only an edge from A to B and not B to A. Thus, we will have (A, B) filled in, but not (B, A).If the nodes are ordered along the rows and columns such that neighbors are listed close to one another, then a matrix plot can be used to visualize clusters, or communities, of nodes.


## Arc plot

![image](https://user-images.githubusercontent.com/84151016/157512142-c58fc82a-30dd-4514-b88d-8aeda605c672.png)


Arc plot is a transformation of the node-link diagram layout, in which nodes are ordered along one axis of the plot, and edges are drawn using circular arcs from one node to another. If the nodes are ordered according to some some sortable rule, e.g. age in a social network of users, or otherwise grouped together, e.g. by geographic location in map for a transportation network, then it will be possible to visualize the relationship between connectivity and the sorted (or grouped) property. Arc Plots are a good starting point for visualizing a network, as it forms the basis of the later plots that we'll take a look at. 


## Circos plot

![image](https://user-images.githubusercontent.com/84151016/157512318-1a74d217-b743-4434-8ee1-61ae597afacd.png)

Circos is a transformation of the ArcPlot, such that the 
two ends of the ArcPlot are joined together into a circle. Circos Plots were originally designed for use in genomics, and you can think of them as an aesthetic and compact alternative to Arc Plots. You will be using a plotting utility that I developed 


nxviz API
called nxviz. Here's how to use it. Suppose we had a Graph G in which we added nodes and edges. To visualize it using nxviz, we first need to import nxviz as nv, and import matplotlib to make sure that we can show the plot later. Next, we instantiate a new nv-dot-ArcPlot object, and pass in a graph G. We can also order nodes by the values keyed on some "key". Finally, we can call the draw function, and as always, we also call plt-dot-show. The code example here shows you how to create an Arc Plot using nxviz, and you'll get a chance to play around with the other plots in the exercises. 




