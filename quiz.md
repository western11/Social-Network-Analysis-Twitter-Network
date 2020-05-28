# Social Network Analysis: Twitter Network Quiz
**INSTRUCTION:**
Open quiz.html or quiz.Rmd to see the plot

## Graph theory and SNA

This section will assess your understanding of Graph theory and SNA

1. Which statement is **TRUE** about graph theory & SNA: (a) Network can be divided into 2 types: directed and undirected. (b) SNA is basicly an implementation of graph theory in human social life. (c) In-degree in directed network, is a two-way relationship between nodes. usually drawn with lines without arrows. (d) Social Network Analysis can be implemented in wide areas, including finding information networks within terrorist group.
  - [ ] (a), (b), and (c)
  - [ ] (a), (b), and (d)
  - [ ] (a), (c), and (d)
  - [ ] all of the above

2. From the picture below. Calculate the *shortest path* between nodes 4 to nodes 13

assets/qz1.png

  - [ ] 6
  - [ ] 5
  - [ ] 7
  - [ ] 8

## SNA metrics (centrality & modularity)

3. Closeness centrality calculate shortest path from specific nodes to every nodes in the network. Thus the more central a node is, the closer it is to all other nodes. From the statements below, choose the **correct** intepretation of closeness centrality.
  - [ ] nodes with high closeness centrality tend to be connected with similliar nodes that also have high closeness centrality value.
  - [ ] nodes with high closeness centrality connect two separated network (subgraph). if the nodes disappear, communication between subgraph will not be possible
  - [ ] nodes with high closeness centrality will spread information faster than any nodes. Its because they have the average length of shortest path to every nodes in network. 

**Question 4 - 5**
Run this code in your workspace
```
qz <- read.csv("data_input/qzexample.csv")
```
From the dataframe, build nodes & edges dataframe then create **directed** network. Name your network as "network_qz"
```
# your code here
# make sure you add as_tbl_graph
nodes_qz <-
edges_qz <-

network_qz <-
```
with igraph package, build network community using cluster_walktrap() function then calculate the modularity.
```
# your code here
```
4. Select the **correct** statements based on your output
  - [ ] High Modularity, the community in network are well separated. they have dense connections between the nodes within community but sparse connections between nodes in different community
  - [ ] Low Modularity, the community in the network actually don't have much difference. Nodes in different community have dense connection. The algorithm having a hard time separating the nodes, will be much better if we use another community detection algorithm
  - [ ] High Modularity, the community in network are well separated. they have sparse connections between the nodes within community but dense connections between nodes in different community
  - [ ] Low Modularity, the community in the network have a lots of difference but the nodes in same community also have sparse connection.

```
# this plot will help you estimate the centrality value
plot(network_qz, edge.arrow.size = 0.5, layout = layout_with_fr)
```
5. Calculate betweenness, closeness, degree centrality and select which node have the highest centrality value consecutively
  - [ ] 8, 4, 5
  - [ ] 7, 5, 5
  - [ ] 7, 4, 2
  - [ ] 8, 5, 5

## Visualization 

**Question 6-7**
Run this code in your workspace
**NOTE:** always use set.seed(123) in the  top of your chunk
```
set.seed(123)
small_qz <- play_smallworld(1,250,3,0.05)
```
Visualize the network using this characteristic: (you need to do this in order)
- in top of your chunk, make sure to input set.seed(123)
- create nodes name by row_number() and create network community using group_louvain() algorithm using mutate()
- filter the nodes that only appear in community 1:2
- using mutate(), calculate eigenvector centrality with centrality_eigen() function (no parameter)
- select 25 nodes with highest eigenvector centarlity value
- Visualize the network using: 
  + ggraph() function with "kk" as the layout
  + geom_edge_fan()
  + geom_node_point()
  + geom_node_text -> only show nodes label with eigenvector centarlity value >= 1. use parameter repel=T
  + theme_graph()

6. from your plot output, select the most similar picture below

  - [ ] a assets/opt_a.PNG
  - [ ] b assets/opt_b.PNG
  - [ ] c assets/opt_c.PNG)


7. Imagine this is a terrorist communication network. They use small community (also called as subgraph) to communicate to avoid suspicion. We are told to find **which node is the most important for spreading information between subgraph**. **Without using any filter and communtiy**, calculate eigenvector, betweenness, closeness, degree centrality and select which pair of nodes that need to be terminated first.
  - [ ] 66, 104
  - [ ] 208, 46
  - [ ] 172, 165
  - [ ] 46, 28
