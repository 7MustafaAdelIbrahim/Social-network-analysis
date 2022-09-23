# Social-network-analysis
     A key technique in modern sociology to investigate social structures through networks and graph theory.
     Networks're everywhere arround you, knowing how to analyze them will open up a new world of possibilities.

From ***online social networks*** such as ***Facebook*** and ***Twitter*** to ***the intersection of biological network, science*** and ***infectious disease*** to ***transportation networks*** which are modeling the connectivity between locations determined by roads, flight or paths connecting them, such as ***bike sharing systems***. 

<p>
<img src= "https://user-images.githubusercontent.com/84151016/157748944-69175325-d053-4bd7-b075-659553ed1ed0.jpg" width="450" height="400">
<img src= "https://user-images.githubusercontent.com/84151016/191648903-8dcbdafd-e07f-4d96-a6d1-e212ac20e09e.png " width="450" height="400">
 </p>
## Network Structure.

Networks-at its core-are described by two sets of items which are nodes and edges for modeling the relationships between entities. These nodes and edges together form a "network", otherwise known in mathematical terms as a "graph". In addition, Nodes and edges can have metadata associated with them.

<img src= "https://user-images.githubusercontent.com/84151016/157509985-077a0c77-1654-4ace-83ff-a78362e31a45.png" width= "400" height= "300">

By modeling your data as a network, you can end up with:
gaining insight into what entities (or nodes) are important, such as broadcasters or influencers in a social network.
Additionally, you can start to think about optimizing transportation between cities.
Finally, you can leverage the network structure to find communities in the network.

For example, let's say there're 2 friends, Hugo and Eric, who met on the 21st of May, 2016. 
<img src= "https://user-images.githubusercontent.com/84151016/157510096-8086ce4f-5b4e-476b-ae52-33d54c7c1325.png "  width="400" height="400">

In this case, the nodes may be "Hugo" and Eric", with metadata stored in a key-value pair as "id" and "age".
The friendship is represented as a line between these 2 nodes, and may have metadata, such as "date", which represents the date on which they first met. 

## Types of graphs. 

#### 1- Undirected graphs.
      Undirected graphs're named as such, as they're comprised of edges that don't have any inherent directionality associated with them.

<img src= "https://user-images.githubusercontent.com/84151016/157510611-7997fef5-399c-4a38-b293-737eee328c21.png" width="400" height="100">

For example, there're social graphs like Facebook. As when one user befriends another, the two are automatically connected with an edge.
This is commonly drawn as a line with no arrows between two circles.

#### 2- Directed graphs.
          There's an inherent directionality associated with the graph.
<img src= "https://user-images.githubusercontent.com/84151016/157510673-ac61cf3f-1cf4-4d89-833d-b71f0bfe0f50.png" width="400" height="100">
Twitter's social graph is a directed network. As the nature of how users interact with one another. One user may follow another, but that other don't.

#### 3- Multi-edge (Directed) graphs.
           Two or more edges connecting the same two vertices within a multigraph.
<img src= "https://user-images.githubusercontent.com/84151016/157510771-6f2d8106-9a71-4ab5-be3f-5c78d61602b3.png" width="400" height="100">
I.e, we may want to model trips between flight, Each flight may be an edge between the pair of airports.

### 4- Self-loops.
     Nodes that are connected to themselves.

<img src= "https://user-images.githubusercontent.com/84151016/157511095-3b20eee5-2ea6-40e4-9a1c-14b6b5c2f983.png" width="400" height="100">
Self-loops can be used in certain scenarios, such as in bike sharing data, where a trip begins at a station and end at the same station.

### Weights on graphs
For collapsing the edges into a single edge that contains a metadata summary of the original. For example, we may want to collapse these three edges into a single one and give them a "weight" metadata. with the value "3", indicating that it was originally 3 edges between the pair of nodes.

<p>
<img src= "https://user-images.githubusercontent.com/84151016/191639572-48709437-5867-40f6-92c5-99df35128ce3.png" width="300" height="200">
<img src= "https://user-images.githubusercontent.com/84151016/191639608-7b8ea93e-5f04-40de-a0ef-44b00774320a.png" width="300" height="200">
</p>

## Network visualization
          A node-link diagrams involving more than a hundred thousand nodes. 
### Irrational vs. Rational visualizations

<img src= "https://user-images.githubusercontent.com/84151016/157511561-dad39835-24a8-46a7-b654-dd9f327d4c7c.png " width="500" height="300">

They purport to show a visual representation of the network, but in reality just show a hairball.
In this section, we are going to look at alternate ways of visualizing network data that are much more rational. 

### Matrix plot

<img src= "https://user-images.githubusercontent.com/84151016/157511613-3f800641-93aa-4190-9487-b48b706d2f47.png " width="500" height="300">

On these slides, the left matrix is the matrix plot of the graph on the right.
In a Matrix Plot, nodes're the rows and columns of a matrix, and cells're filled in according to whether an edge exists between the pairs of nodes.

### In an undirected graph. 

<img src= "https://user-images.githubusercontent.com/84151016/157511853-120b8959-d891-4283-87aa-ce5b9b39bc7c.png " width="800" height="300">

The matrix is symmetrical around the diagonal, which I've highlighted in gray. I've also highlighted one edge in the toy graph, edge (A, B), which is equivalent to the edge (B, A).Likewise for edge (A, C), it's equivalent to the edge (C, A), as there's no directionality associated with it. 

### Directed matrices

<img src= "https://user-images.githubusercontent.com/84151016/157511979-4150c688-f685-4491-be1d-33e119c644d2.png " width="600" height="300">

If the graph were a directed graph, then the matrix representation is not necessarily going to be symmetrical. In this example, we have a bidirectional edge between A and C, but only an edge from A to B and not B to A. Thus, we will have (A, B) filled in, but not (B, A).If the nodes are ordered along the rows and columns such that neighbors are listed close to one another, then a matrix plot can be used to visualize clusters, or communities, of nodes.

## Arc plot

<img src= "https://user-images.githubusercontent.com/84151016/157512142-c58fc82a-30dd-4514-b88d-8aeda605c672.png " width="600" height="300">

Arc plot is a transformation of the node-link diagram layout, in which nodes are ordered along one axis of the plot, and edges are drawn using circular arcs from one node to another. If the nodes are ordered according to some some sortable rule, e.g. age in a social network of users, or otherwise grouped together, e.g. by geographic location in map for a transportation network, then it will be possible to visualize the relationship between connectivity and the sorted (or grouped) property. Arc Plots are a good starting point for visualizing a network, as it forms the basis of the later plots that we'll take a look at. 

## Circos plot

<img src= "https://user-images.githubusercontent.com/84151016/157512318-1a74d217-b743-4434-8ee1-61ae597afacd.png " width="600" height="300">

Circos is a transformation of the ArcPlot, such that the two ends of the ArcPlot are joined together into a circle. Circos Plots were originally designed for use in genomics, and you can think of them as an aesthetic and compact alternative to Arc Plots. You will be using a plotting utility that I developed 

## Important nodes.
          How might we tell what an important node is?

Many metrics we can use to evaluate the importance of a node. But, there're 2 concepts more important to be introduced. The 1st is called "degree centrality", the other is called "betweenness centrality". Let's take a look at the following two "star graphs". If you looked at the center nodes, which center node of the two graphs might be considered "more important"?

<img src= "https://user-images.githubusercontent.com/84151016/157513367-32142d60-fc44-4d1c-abeb-9338f03081cd.png " width="500" height="300">

If you chose the left graph, then you'd be very justified in doing so!
In the majority of situations, we would consider the left graph's center node to be more important than the right graph's center node, because it is connected to more nodes. Being connected to other nodes means other nodes are considered a neighbor of that node. From the concept of neighbors, we can now introduce the concept of "degree centrality".

## Degree centrality
It's simply defined as the number of neighbors that a node has divided by the total number of neighbors that the node could possibly have.
<img src= "https://user-images.githubusercontent.com/84151016/191648130-cb804f55-2139-4aa8-8909-0e0cbfe0e09e.png" width="700" height="400">

#### There're 2 scenarios possible here: 
##### If self-loops're allowed. 
such as in a network mapping of all bike trips in a bike sharing system, then the number of neighbors that I could possibly have, is every single node in the graph, including myself.

##### On the other hand, if self-loops are not allowed.
such as in the Twitter social network where, by definition, my account cannot follow itself, then the number of neighbors I could possibly have, is every other node in the graph, excluding myself.
In real life, examples of nodes in a graph that have high degree centrality might be: Twitter broadcasters. users that are followed by many other users, airport transportation hubs, such as the New York, London or Tokyo airports nd finally, disease super-spreaders, who are the individuals that epidemiologists would want to track down to help stop the spread of a disease. Let's now introduce the NetworkX API.

## Betweenness centrality
Before we talk about that, we need to extend our knowledge with one key concept such as ***all shortest paths*** .
#### ***How to find the shortest path between any pair of nodes?!*** 
Using any search strategies, such as the ***breadth-first search (BFS) algorithm***. Imagine we used the BFS to find every shortest path between every pair of nodes. What we would get back is the set of "all shortest paths" in a graph. In other words, ***"all shortest paths"*** are the set of paths in a graph, such that each path is the shortest path between a given pair of nodes, done for all pairs of nodes. Now we can introduce 

The definition of ***betweenness centrality*** is defined as ****the number of shortest paths in a graph that pass through a node divided by the number of shortest paths that exist between every pair of nodes in a graph***.
This metric captures a different view of importance - in essence, it captures bottleneck nodes in a graph, rather than highly connected nodes; this will become much clearer as we go on.
<img src= "https://user-images.githubusercontent.com/84151016/191648394-672f52fe-7f07-458a-adac-ea05af79d834.png" width="700" height="400">

#### Where might betweenness centrality useful?

One example would be individuals that bridge between two communities, say, an individual bridging liberal-leaning and conservative-leaning Twitter users.
Alternatively, consider the internet, where there are crucial links that bridge two networks of computers. If we removed those crucial nodes in the internet, then information will not flow (or at least not as easily) between subnetworks. 


Examples
Let's look at the Singapore subway system to make this more concrete. Take a look at two sets of stations that I have highlighted. In the south, there's a cluster of stations in the central business district that serve as connectors between different lines, but there's also this other station called Jurong East, which is only connected to three other stations, but serves as a major transit connector point between the red and the green lines. [Source](http://www.seacitymaps.com/singapore/singapore_mrt_map.jpg)

<img src= "https://user-images.githubusercontent.com/84151016/157516172-9b6bc3de-026d-4cac-9c6a-c98588087d34.png" width="700" height="700">

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

## References.

https://www.sciencedirect.com/topics/social-sciences/social-network-analysis
