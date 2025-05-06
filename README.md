#Objective
Traverse a workflow graph represented as a Directed Acyclic Graph (DAG), ensuring:

A node executes only after all its parent nodes are executed.

Child nodes are executed in parallel, if multiple.

#Tools/Libraries Used
Python 3.10+

collections.defaultdict for graph representation.

threading module to simulate parallel execution of child nodes.

 #Assumptions
Input is well-formed as per given format (e.g., "1:Node-1" and "1:2").

Node with key 1 is always the root/start node.

The graph does not contain cycles (DAG).

We simulate parallelism using threads—no need for strict synchronization or shared state.

#Design Decisions
Graph Representation: Adjacency list with defaultdict(list) for forward edges; in_degree map to track dependencies.

Execution Strategy:

Traverse graph via DFS from root.

Before visiting a node, ensure in-degree is zero (i.e., all parents executed).

Thread each child node’s execution if all its parents have completed.

Thread Safety: No shared mutable state modified concurrently—so basic thread model suffices.

# Output Format
Prints each node name as it's executed.

Final line prints total number of unique nodes.
