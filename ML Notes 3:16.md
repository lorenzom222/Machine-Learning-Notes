ML Notes 3/16.md

Graphs and Cycles

Tree Decomposition


The Ford-Fulkerson method is an algorithm used to solve the maximum flow problem in a network. The goal of the algorithm is to find the maximum possible flow that can be sent through the network from a source node to a sink node.

The algorithm starts with an initial flow of zero, which means that no flow is currently being sent through the network. The flow value is represented by a function f(u,v), which gives the amount of flow that is being sent from node u to node v.

At each iteration, the algorithm tries to increase the flow value by finding an "augmenting path" in the residual network Gf. The residual network Gf is a modified version of the original network G, which takes into account the current flow that is already being sent through the network.

An augmenting path is a path in Gf from the source node to the sink node, where the amount of flow that can be sent along the path is not limited by the current flow in the network. In other words, an augmenting path is a path where we can increase the flow value without violating the capacity constraints of the edges in the network.

Once we have identified an augmenting path in Gf, we can easily identify specific edges in G for which we can change the flow. We increase the flow along the edges of the augmenting path by the maximum amount possible, which is equal to the minimum capacity of the edges along the path.

We repeat this process of finding augmenting paths and increasing the flow until we can no longer find any augmenting paths in Gf. At this point, we have found the maximum possible flow that can be sent through the network from the source node to the sink node.


What does this mean: Once we have identified an augmenting path in Gf, we can easily identify specific edges in G for which we can change the flow. 

In the Ford-Fulkerson algorithm, once we have identified an augmenting path in the residual network Gf, we can increase the flow along this path in the original network G. The augmenting path in Gf indicates a path from the source node to the sink node where there is available capacity for increasing the flow.

The residual network Gf is created from the original network G by subtracting the flow already being used on each edge in the network from its capacity. So, if an edge has a capacity of 10 units and the current flow being used on the edge is 5 units, then the residual capacity of the edge in Gf will be 5 units. An augmenting path in Gf is a path from the source node to the sink node where all edges have positive residual capacity.

Once we have identified an augmenting path in Gf, we can follow the path in the original network G and increase the flow along the path by the minimum residual capacity of the edges in the path. This will ensure that the new flow does not violate any capacity constraints and will increase the total flow value. By identifying the augmenting path in Gf, we can easily identify the specific edges in G that need to be updated to increase the flow.


This statement is defining the residual network Gf induced by a flow f on a given flow network G.

The residual network Gf is a new network consisting of the same set of vertices V as in the original flow network G, but with a different set of edges Ef. The edges in Ef are determined by considering each edge (u,v) in G and checking whether it has remaining capacity to admit more flow. If the capacity is not fully utilized by the current flow f (i.e., cf(u,v) > f(u,v)), then we add a new edge (u,v) to the residual network Gf with a capacity equal to the residual capacity cf(u,v) - f(u,v).

Therefore, the set of edges Ef in Gf consists of those edges in G that have residual capacity, as determined by the flow f. In other words, Ef contains all edges (u,v) in G such that cf(u,v) - f(u,v) > 0.

Overall, the residual network Gf represents the remaining capacity of edges in G to admit more flow, given the flow f that is currently flowing through the network. The residual network is a useful tool for algorithms that aim to find the maximum flow in a network, as it allows them to explore different flow paths and adjust the flow as needed to reach the maximum flow.


Why ResNets?

This passage is explaining the intuition behind the definition of augmenting paths, which are a key concept in the Ford-Fulkerson algorithm for solving maximum flow problems in flow networks.

When we want to increase the flow in a flow network along a particular path, we need to find a path that has enough residual capacity to accommodate the additional flow. 

An augmenting path is a path in the residual network that connects the source and the sink and has positive residual capacity for every edge along the path. 

This means that we can increase the flow in the network along this path by a certain amount, which is equal to the minimum residual capacity along the path.

The passage goes on to explain that the intuition behind this definition follows from the definition of the residual network. 
When we want to increase the flow along a particular path, we push flow on the forward edges in the residual network, which correspond to increasing the flow in the original network. 

However, to ensure that the flow remains a valid flow, we need to simultaneously decrease the flow along the reverse edges in the residual network, which correspond to decreasing the flow in the original network. Pushing flow along the reverse edges in the residual network is also known as cancellation, because it cancels out the flow that was previously sent along the corresponding forward edge.

Overall, the concept of augmenting paths provides a way to increase the flow in a flow network and move closer to the maximum flow. The Ford-Fulkerson algorithm works by repeatedly finding augmenting paths and increasing the flow along those paths until no more augmenting paths can be found.
