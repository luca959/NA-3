# Network Analysis

## Third Assignment - Network robustness

In this third and final assignment we will test robustness of networks using different kind of attacks.

First, to check the correctness of our code, we will test robustness on small graphs, then we will test our real network.

<br>

We will use different kind of attacks:

- **random attacks** - nodes will be removed at random
- targeted attacks:
  - **highest degree** - nodes with highest degree will be removed
  - **highest betweenness** - nodes with highest betweenness will be removed
  - **highest closeness** - nodes with highest closeness will be removed
  - **highest pagerank** - nodes with highest pagerank will be removed

> During all the attacks we will consider the largest connected component of the graph.

<br>

Our analysis will be based on the following metrics:

- **size of the largest connected component** - we expect this metric to decrease during the attacks
- **diameter** - we expect this metric to increase (before dipping) during the attacks

### 1. testing on small graphs

In this first part of the assignment we will test the robustness of the network on small graphs. We will use the following graphs:

- Erdos-Renyi graph
- Watts-Strogatz graph

## 1.1. Erdos-Renyi graph

The Erdos-Renyi graph is a mathematical model for generating random graphs.
The graph is constructed by randomly assigning edges between a fixed number of nodes and it's based on two parameters: the total number of nodes in the graph, denoted as "n" and the probability of any pair of nodes being connected by an edge, denoted as "p".   
  
<strong>n</strong>:100 |
<strong>p</strong>:0.1
![erdos-renyi-n100-p0.1](./src/erdos-renyi-n100-p0.1.png)
  
These graphs show the change of size and diameter during an attack of the network.  
The x-axis represents the number of nodes removed from the network, the y-axis represents the size of the largest connected component and the diameter.

As we can see, the size of the largest connected component decreases during the attack, while the diameter for a while increases then decreases.

Another important thing to notice is that Erdos-Renyi graph is very robust as a matter of fact to destroy compleately the graph we have to remove roughly 60% of the nodes.

The 5 attacks can be diverged in two categories: 
- Fast attack: Closeness, Betweenness and Degree
- Slow attack: Random and Pagerank

## 1.2. Watts-Strogatz graph

The Watts–Strogatz model is a random graph generation model that produces graphs with small-world properties, including short average path lengths and high clustering.
It's defined by three parameters: `n`, `k` and `p`. `n` is the number of nodes, `k` is the number of nearest neighbors and `p` is the probability of rewiring each edge.  

<strong>n</strong>:100 |
<strong>p</strong>:0.1 |
<strong>k</strong>:5

![watts-strogatz-n100-p0.1-k5](./src/watts-strogatz-n100-p0.1-k5.png)

As concerns for the Watts-Strogatz graph, is less robust than the Erdos-Renyi graph. In fact, to destroy compleately the graph we have to in the worst case remove roughly 50% of the nodes and in the best case 20%.

On the other hand the behavior of the size of the largest connected component and the diameter is similar to the Erdos-Renyi graph.

## 2. Testing on the Real Retwork

**BCSPWR10**, a real-world dataset containing a representation of the entire U.S. electrical power grid network.  
The BCSPWR10 Network has the following specifications:  
**Node**: 5300  
**Edges**: 8271
