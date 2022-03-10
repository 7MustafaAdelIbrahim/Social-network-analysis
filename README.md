# Social-network-analysis
     A key technique in modern sociology to investigate social structures through networks and graph theory.


From ***online social networks such as Facebook and Twitter to transportation networks such as bike sharing systems*** , networks are everywhere and knowing how to analyze them will open up a new world of possibilities for you as a data scientist.

![id-program-network](https://user-images.githubusercontent.com/84151016/157748944-69175325-d053-4bd7-b075-659553ed1ed0.jpg {width=40px height=400px})

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
called nxviz. Here's how to use it. Suppose we had a Graph G in which we added nodes and edges. To visualize it using nxviz, we first need to import nxviz as nv, and import matplotlib to make sure that we can show the plot later. Next, we instantiate a new nv-dot-ArcPlot object, and pass in a graph G. We can also order nodes by the values keyed on some "key". Finally, we can call the draw function, and as always, we also call plt-dot-show.

## Important nodes
          How might we tell what an important node is?
          There will be two concepts that I will introduce you to. 
          The 1st is called "degree centrality", and the 2nd is called "betweenness centrality". Let's take a look at the following two "star graphs".

If you looked at the center nodes, which center node of the two graphs might be considered "more important"?

![image](https://user-images.githubusercontent.com/84151016/157513367-32142d60-fc44-4d1c-abeb-9338f03081cd.png)

If you chose the left graph, then you'd be very justified in doing so!
In the majority of situations, we would consider the left graph's center node to be more important than the right graph's center node, because it is connected to more nodes. Being connected to other nodes means other nodes are considered a neighbor of that node. From the concept of neighbors, we can now introduce the concept of "degree centrality".

### Degree centrality
The degree centrality metric is one of many metrics we can use to evaluate the importance of a node, and is simply defined as the number of neighbors that a node has divided by the total number of neighbors that the node could possibly have.

![image](https://user-images.githubusercontent.com/84151016/157513652-b34ed3a6-1d34-48c0-9831-f181572a99a0.png)


There are two scenarios possible here: 
#### If self-loops are allowed. 
such as in a network mapping of all bike trips in a bike sharing system, then the number of neighbors that I could possibly have is every single node in the graph, including myself.

#### On the other hand, if self-loops are not allowed.
such as in the Twitter social network where, by definition, my account cannot follow itself, then the number of neighbors I could possibly have is every other node in the graph, excluding myself.In real life, examples of nodes in a graph that have high degree centrality might be: Twitter broadcasters, that is, users that are followed by many other users; airport transportation hubs such as the New York, London or Tokyo airports; and finally, disease super-spreaders, who are the individuals that epidemiologists would want to track down to help stop the spread of a disease. Let's now introduce the NetworkX API.

## Betweenness centrality
   Before we talk about that, we need to extend our knowledge with one key concept such as all shortest paths.

### All shortest paths

That of "all shortest paths". In the section below, we'll take about how to find the shortest path between any pair of nodes, using the breadth-first search algorithm. Imagine now we used the BFS to find every shortest path between every pair of nodes. What we would get back is the set of "all shortest paths" in a graph.
In other words, "all shortest paths" are the set of paths in a graph, such that each path is the shortest path between a given pair of nodes, done for all pairs of nodes. Now we can introduce 

The definition of betweenness centrality is defined as the number of shortest paths in a graph that pass through a node divided by the number of shortest paths that exist between every pair of nodes in a graph. This metric captures a different view of importance - in essence, it captures bottleneck nodes in a graph, rather than highly connected nodes; this will become much clearer as we go on.

![image](https://user-images.githubusercontent.com/84151016/157515953-4545f816-f9ad-4bac-bf94-58217f6cefc3.png)


#### Where might betweenness centrality useful?

One example would be individuals that bridge between two communities, say, an individual bridging liberal-leaning and conservative-leaning Twitter users.
Alternatively, consider the internet, where there are crucial links that bridge two networks of computers. If we removed those crucial nodes in the internet, then information will not flow (or at least not as easily) between subnetworks. 


Examples
Let's look at the Singapore subway system to make this more concrete. Take a look at two sets of stations that I have highlighted. In the south, there's a cluster of stations in the central business district that serve as connectors between different lines, but there's also this other station called Jurong East, which is only connected to three other stations, but serves as a major transit connector point between the red and the green lines.

![image](https://user-images.githubusercontent.com/84151016/157516172-9b6bc3de-026d-4cac-9c6a-c98588087d34.png)

[Source:] (http://www.seacitymaps.com/singapore/singapore_mrt_map.jpg)

Let's take a look at the code for computing betweenness centrality. Let's say we have a graph G that is a barbell graph. We can create this graph 
by using one of NetworkX's graph generators, nx-dot-barbell_graph, with m1 being the number of nodes in the barbell ends, and m2 being the number of nodes in the barbell bridge. To get the betweenness centrality, we can call on NetworkX's betweenness_centrality function, which takes in a graph object G as an argument. What that function returns is a dictionary, just like the degree_centrality function, in which the nodes are the keys and their betweenness centrality scores are the values. 
You might notice that some of the nodes here have betweenness centrality scores of "0". That's because they are located at the ends of the barbell graph, and the nodes within each end are fully connected with one another. Therefore, with the exception of the bridge node and the two other nodes it is connected to, there's no shortest path that has to run through any of those nodes to get to other nodes. 

![image](https://user-images.githubusercontent.com/84151016/157516498-fc81fff0-ee87-48c3-8383-f2c0d11c271b.png)

## Number of neighbors
for figuring out the number of neighbors that a node has. Suppose we had a star graph, in which node 1 was connected to every other node. NetworkX graphs expose a G-dot-neighbors function, which allows us to get back a list of neighbors for a given node in a graph. For example, if I do G-dot-neighbors(1), I will get back the neighbors of node 1. Likewise for node 8. If I pass in a node that doesn't exist in the graph, I'll get back a long error trace with a final line that reads, "NetworkX Error: The node [n] is not in the graph. "NetworkX also provides 
the degree_centrality function, which takes in a graph object as an argument, and returns a dictionary in which the key is the node and the value is the degree centrality score for that node. With the degree centrality function, self-loops are not considered. 

## Graph algorithms
          Path-finding has many important applications. 

One example is optimization problems, such as finding the shortest transportation path between two nodes.
It's also important in modeling the spread of things, such as the spread of disease in an outbreak, or information spread in a social network.

![image](https://user-images.githubusercontent.com/84151016/157514321-0382dcfa-c70b-4930-9095-69df00e912ba.png)

     How do we find out whether there's a path between two nodes? 
     If there's a path, how do we find out what the shortest path is? 
     
One way we can do so is by the "breadth-first-search algorithm". 

### Breadth-first search (BFS)
          In its essence, breadth-first-search algorithm is to find out the shortest path.
 
The breadth-first search algorithm was first developed in the 1950s as a way of finding the shortest path out of a maze. How does this algorithm work? Suppose we have the network above, comprised of 11 nodes, and we want to find the shortest path between the yellow and red nodes.

The algorithm essentially works as such.
- If we start at the yellow node, 
   - We first ask for the yellow node's neighbors. 
   - then ask if the destination node is present in the set of yellow node's neighbors.
   - If not, we continue on. Going out a second degree of separation, 
         we ask for the neighbors of our neighbors. The destination node is still not present, so we continue on. 

On our 3rd degree of separation out, we see that the destination node is present. At this point, we can stop and ignore the next degree of separation. Note that there was one other path possible, but it was longer. As such, with the breadth-first-search algorithm, we have achieved our goal of finding the "shortest" path between the pair of nodes. 

Let's quickly review some code that will help you with the following exercises. Say we have a graph G. As a good habit, let's check first for the number of nodes and edges present. Recall that we can do len(G-dot-edges) and len(G-dot-nodes), and see that there are 57 edges between 20 nodes. Let's see if we can find a path between nodes 1 and 19. 
If we do G-dot-neighbors(1), we get back a list containing the nodes [10, 5, 14, 7] as the neighbors of 1. Let's go one degree out, to the first node in the list of node 1's neighbors, which is node 10. Now, let's check the neighbors of 10: note that we have 1, which is correct, and then 19, and then a whole slew of other nodes. Since 19, our destination node, is present in the neighbors of node 10, we can stop there. If 19 wasn't there, we would go on to check the neighbors of node 5, which was the next node in the list of node 1's neighbors.



## Network structures. 
     Finding interesting structures within network data.

We'll take about essential concepts such as ***cliques, communities, and subgraphs***, which will leverage all of the skills you acquired. 
By the end of this chapter, you'll be ready to apply the concepts you've learned to a real-world case study. 

Video1
 feeling challenged and energized for the coming set of ideas!

We're now going to explore the concepts of structures and subgraphs, using NetworkX.

particularly on path finding and the use of neighbors. Before we go to the technical stuff, let's think about a real-life scenario.
Cliques
Have you ever been in a clique? How would you characterize the clique? It probably was comprised of people who knew everybody else in the group to a pretty strong degree.
Now imagine if there was another new person not originally part of the clique that joined in , this group, it wouldn't feel like a "clique", because the new person doesn't really know everybody else, and vice versa.

In network theory, a "clique" is essentially defined on the social version of a clique: a set of nodes that are completely connected by an edge to every other node in the set.

It is, then, a completely connected graph. What might be the "simplest clique"?
By the definition of a clique, an edge is the simplest clique possible.

what would be the simplest "complex clique"? 
"3 nodes fully connected", or, in other words, "a triangle 
Triangle Applications
What are some applications of finding "triangles" in a network?
one example may be in friend recommendation systems. For example, if A knows B and A knows C, but B and C are not yet connected, then there's a good chance that B knows C as well, and may want to be connected online, by doing what we call triangle closures.
Clique Code
How might you write code that finds all triangles that a node is involved in? but I will give you a few coding hints to launch you into them. Suppose you had a graph G, and you wanted to iterate over every pair of nodes, and not only every edge. Rather than writing a double for-loop, you might want to use the combinations function from the Python itertools module. In this way, your for loop can iterate over every pair of nodes in the network, by using the following code: for n1, n2 in combinations(sequence, size of combinations) - so in this case it's G-dot-nodes and 2 because we wanted pairs of nodes. In the logical code block just after, we can do whatever we need to do with the pairs of nodes. In this demo code above, I've just decided to print them
Video2
Maximal cliques
Maximal cliques are defined as such: they are a clique, but that clique cannot be extended by adding another node in the graph.
For example, the sub-clique of the 3 green nodes can be extended by one blue node to form a larger clique. As such, these 3 green nodes do not form a "maximal clique" in the graph. On the other hand, the four nodes
connected as a clique together cannot be extended and still remain a clique, as the remaining node is not fully connected to the other four nodes. As such, these four nodes constitute a "maximal clique".
The concept of maximal cliques has its uses in community finding algorithms. Without going into the myriad of details possible, I hope to define at a basic level
Communities
what a community is. Cliques form a good starting point for finding communities, as they are fully connected subgraphs within a larger graph. By identifying these maximal cliques, one naive way of identifying communities might be identifying the unions of maximal cliques that share some number of members, but are also of some minimum size.
 NetworkX API
NetworkX provides a function for finding all maximal cliques, which is the find_cliques function. Remember this as you go forward, that find_cliques will not just find any clique but the set of maximal cliques.
Maximal cliques
Let's bring back the barbell graph from before. If we apply the nx-dot-find_cliques function, we will find that it returns a generator, which we can iterate over, but it doesn't return the list of maximal cliques. To get the list of maximal cliques, we need to cast that as a list.
It should be clear to you that there are two maximal cliques of size 5 in this graph. What might be less intuitive is that there are
two maximal cliques of size 2 - these are the edges between nodes 4 and 5, and nodes 5 and 6. Recall that edges are also a clique.
Video3
Subgraphs
"subgraphs" in the context of cliques. When you have a large graph, and you want to visualize just a small portion of it, it can be helpful to extract those nodes and their associated edges as a separate graph object.
For example, you might want to visualize a particular path through the network, or you might want to visualize a particular community or clique.
Alternatively, you might just want to explore the structure of the graph around a node going out a number of degrees of separation. In all of these scenarios, it's useful to be able to "slice out" the nodes and edges of interest, and visualize them.
Let's take a look at how we might be able to do this. Let's say I have a graph G, made by the Erdos-Renyi graph generator in NetworkX. I can construct it by using the nx-dot-erdos_renyi_graph function, passing in n equals 20 (for the number of nodes in the graph), and p equals 0-point-2 (for the probability that an edge exists between a given pair of nodes). The graph is generated probabilistically, and in this instance, has 20 nodes, connected by 37 edges. Let's say I'm interested in plotting node 8 and its neighbors. I can first initialize a list called nodes, comprised of the neighbors of node 8. I can then append the node 8 to the list. To get the subgraph, of the five nodes, I can use the
G-dot-subgraph function, passing in the nodes list, and assign the result to a new graph called G_eight-dot-G_eight will have the nodes 8 and its neighbors, and the four edges that connect node 8 to its neighbors. In addition, it will contain the edges that exist between node 8's neighbors, such as the edge between node 2 and 10. If we check the data type of both graphs, we'll notice that they will both have the same data type.
We can draw the subgraph of those nodes by using a familiar function, nx-dot-draw. Note that apart from passing in the graph object G_eight, we can also tell the draw function to draw the graph with node labels as well, to help with visualization.




## References.

https://www.sciencedirect.com/topics/social-sciences/social-network-analysis


