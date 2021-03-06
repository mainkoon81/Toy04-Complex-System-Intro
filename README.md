## Introduction
<img src="https://user-images.githubusercontent.com/31917400/65374429-a3e38680-dc81-11e9-887a-ce3802f0daa8.jpg" />

## Four concepts explaining a Complex System
__1.Systems within a System:__ 
 - Herbert Simons gives us this definition; "A system that can be analyzed into many components having relatively many relations among them, so that the behavior of each component depends on the behavior of others."
 - Jerome Singer tells us; "A system that involves **numerous interacting agents** whose aggregate behaviors are to be understood. **`Such aggregate activity is nonlinear`**, hence it cannot simply be derived from summation of individual components behavior."
 - the Emergence Theory? Put things together...Something emerges. The emergence is the special phenomenon that results from the interaction of mutiple elements. Walking is the emergence. It's not about double hopping of two legs. It's a synergistic interaction between two legs. 

-> `Elements are nested inside of subsystems (Multi-dimensional property) and many elements on many different scales with all of these levels affecting each other.` How relationship between multiple parts give rise to the **collective behaviors** of a system ? 
<img src="https://user-images.githubusercontent.com/31917400/65376419-6f7ac500-dc97-11e9-889f-215a08fda75a.jpg" />

__2.Nonlinearity + Chaos:__
 - Nonlinearity arises from the fact that when we put multiple things together, the result may not necessarily be a simple addition of each element's property in isolation. This is Post-Newtonian! 
 
-> `Some small change in input value to the **system** can (via dynamics of feedback loops) trigger a large sysmetic effect that is a **combined effect** greater/less than the simple sum of each element's property because of their interdependent nature.` This is referred to as **sensitivity of initial conditions** which is the central idea of the Chaos theory. 
<img src="https://user-images.githubusercontent.com/31917400/65376608-e1540e00-dc99-11e9-8c0f-a4c4929ef4e1.jpg" />
 
__3.Network:__
 - the Graph Theory?
 
-> `The connection density`(**degree**) `or connection pattern`(**position**: How things flow in the network) `defines the **system** as opposed to the element's properties.` 
<img src="https://user-images.githubusercontent.com/31917400/65376769-b66ab980-dc9b-11e9-83e2-e2e0b4a37910.jpg" />

__4.Adaptation + Self Organization:__
 - When a certain degree of **autonomy** that each element has is coupled with the loosened **"top-down centralized mechanism"** for coordinating the whole system, the elements can synchronize their state locally, resulting in the **emergence of the system from the "bottom-up"**...the Agent-based modeling takes the bottom-up approach? 
 - the Game Theory? Cooperation + Competition
 - To model how the system evolves over times, we give the small rules to each eleement and let them develop and see what happens. We have computers that can simulate this process. This is the "Agent Based Modeling". What macro pattern emerges over time?  

-> `This is the system of diversity and evolution.`
  - `Heterogeneity` with high levels of **diversity**!!! such as ..ecosystems...multicultural societies
  - `Being subject to the evolutionary force` of Selection & Replication...which makes an **evolution**!!!
<img src="https://user-images.githubusercontent.com/31917400/65376982-84a72200-dc9e-11e9-81e5-7a8630b82bcd.jpg" />

Complexity Theory as a generic framework for modeling is the composite of the four perspectives discussed above.

---------------------------------------------------------------------------------------------------------------
## Network Analysis
<img src="https://user-images.githubusercontent.com/31917400/69678662-1ddb2600-109e-11ea-93f9-dbcd9801e3e8.jpg" />

 - Undirected: `Graph01 = nx.Graph()`
 - Directed: `Graph01 = nx.DiGraph()`
 - Multiple relation: `Graph01 = nx.MultiGraph()`
```
import networkx as nx
Graph01 = nx.Graph()

Graph01.add_node("A")
Graph01.add_nodes_from(["B","C"])
Graph01.add_edge('A', 'B', weight=2, sign="+", relation="friend")
Graph01.add_edge('B', 'C', weight=6, sign="-", relation="enemy")
```



## Networks in Complex System
Complex systems are networks of agent. They made of many heterogeneous and diverse agents or agent parts that interact in various ways. An agent can actually be a complex system on its own and it contain properties, that is to say, agents can be made of other agent or made from agent parts; however, Complex systems are difficult to define because they contain many irregular properties. 

### How to simplify complexity in the Network?
 - Global Pattern?
   - Degree Distribution, Diameter, etc.
 - Segregation Pattern?
   - ...
 - Local Pattern?
   - Clustering, etc.
 - Positions in the Network?
   - Centrality, Neighborhood, etc.  
 
> Why Network?
It's a setting. Things like trades good and services, most markets are actually not centralized but occur between different parties and it's bilateral relationships. Sharing a favor, risk, transmission of viruses, opinion, job hunting information..often through somebody you knew.. how do you choose who you vote for? How do you make decisions about products? A lot of time you're talking to different individuals, what did they hear? how did you hear about your information? Political alliances can be represented in these networks, trade alliances, there's all kinds of, of different settings where **network structure is very important**. 
 - The networks actually influence the behavior. So if we look at crime, employment, people's investment in human capital, education, how they vote, etc. are embedded in these settings and are influenced by the network structure. Networks come in different sizes and shapes, what they look like is going to be very important in understanding what the outcomes are. 
 - What to ask?
   - What we know about the networks?
     - their formation from different perspectives?
     - What's the relationship between `how dense a network is` and `what the outcomes are`?
   - Why Modeling?
     - Predict from the sample
     - Statistical Estimation

<img src="https://user-images.githubusercontent.com/31917400/70949674-51ceb900-2056-11ea-8f92-2099b1a3f1fe.jpg" />

## [Part 1]: Background and Fundamentals
Definitions and Characteristics of Networks?

### Static Network
<img src="https://user-images.githubusercontent.com/31917400/70853188-90bc0d80-1ea2-11ea-9ddd-6a773829911b.jpg" />

### >Network Property: 1.Diameter(= AVG path length?)  
Global property? How close are nodes? How fast will information spread? 
 - `Diameter` refers to the largest shortest path!
   - which node couple in love takes the longest path?
   - Diameter can be prone to outliers. 
     - It could happen to be one pair of nodes which are extremely far from each other, but others are relatively well connected to each other.
 - `Degree` refers to the size of spouses the node has! octopus! 
 - If the network is unconnected, See larger Network component to calculate the diameter!
 - Before calculating diameter, we need to ensure that **there's actually paths from any two nodes to each other with a high probability**. So, with a high probability, you can get from any node to any other node. 
 - Plus, the network should not be too complete!
   - it should not be as if every node just reaches every other node in merely a **path of length one**. 
     - `degree(n) / n` ~ `0` of course!
   - the `degree(n)` should be at least greater than `C x log(n)`
     - `degree(n) > C*log(n)`
   - Then for `large n`, the **diameter** is approximately proportional to **`log(n) / log(degree(n))`**

`G(n, p)`: In the `n`nodes network, **each link is formed independently** with some probability `p`.
<img src="https://user-images.githubusercontent.com/31917400/70911975-e3b0d480-200a-11ea-8aff-7dba723cb6b6.jpg" />

### Tree
<img src="https://user-images.githubusercontent.com/31917400/70918275-c550d600-2016-11ea-88fe-d92ad28e455c.jpg" />

### Random Network ???
<img src="https://user-images.githubusercontent.com/31917400/70924861-2cc05300-2022-11ea-8eaf-1a2284e2e9bd.jpg" />

### >Network Property: 2.Degree Distribution
<img src="https://user-images.githubusercontent.com/31917400/70927222-80cd3680-2026-11ea-856e-0dd9a18dded8.jpg" />

"Fat Tails" means the observe network usually have too many nodes with too high or too low degrees.
  <img src="https://user-images.githubusercontent.com/31917400/70927534-0c46c780-2027-11ea-8b89-644af00093eb.jpg" />

### >Network Property: 3.Clustering
Local property?? 
 - begin to think about how dense is a network at a local level? 
 <img src="https://user-images.githubusercontent.com/31917400/70930637-8d08c200-202d-11ea-964b-f0010705a9d6.jpg" />

### >Network Property: 4.Centrality
Positioning the nodes in the Network? Which node should be on the center in the network? 
 - __degree__ (how many connected?)
   - Degree based centrality = `degree / (n-1)`.
 - __close-ness__ (how closely connected?)
   - Closeness based centrality = `(n-1) / ΣI(i,j)` w.r.to `j` where `I(i,j)` means the shortest path length b/w node i and j=1,2,3,... 
 - __between-ness__ (how much contributing to the others connections?)
   - what's the fraction of shortest paths that `k` lies on between other node? In order to build a path, each node need to go through somebody(a third party which is our protagonist`k`) that they were connected with. It measures how powerful the `k` is as an intermediary connecting other families on pairs between them.
   - Betweenness based centrality = `Σ #(i,j) that "k" lies on / #(i,j)` / `(n-1)(n-2)/2`
 - __Eigenvectors__ (your importance comes from being connected to other important Nodes)
   - the centrality is proportional to the sum of the neighbor centralities.
   - Eigenvector based centrality = `C * Cen_vector_i = Node matrix * Cen_vector_j`
<img src="https://user-images.githubusercontent.com/31917400/70996412-9c8a1880-20ca-11ea-9163-c6d164117f59.jpg" />







### More about Random Network


### Formation


### Diffusion


### Learning


### Games


 






---------------------------------------------------------------------------------------------------------------
## How do `individual interactions` aggregate to produce `collective behavior`? and how the collectives behave as an organic whole?
<img src="https://user-images.githubusercontent.com/31917400/69735709-144ad000-1129-11ea-815b-e9c9adb9d2f6.jpg" />

> What does Individial Interaction generate?
 - Patterns of segregation
 - Patterns of inequality
 - Emergence of collective movement
 - Norms that change across time?????
 - **Agent-Based Simulation** helps explain the complex processes generated by individual interactions.
   - We build a system by giving individuals rules and observing the outcome. 

### EX_1. Segregation Model 
<img src="https://user-images.githubusercontent.com/31917400/70067714-9c781c00-15e6-11ea-8f84-866dbc2c09f4.jpg" />

Thomas Schelling was asking, where does segregation come from, and how can we prevent it? **racism? unfair housing practices?** But we also have this intuition that `individuals` produce that phenomenon (Individuals have preferences!). What if we removed all those external forces? traditional explanations of where segregation comes from? Schelling asked the question about the fundamental origins of where segregation comes from. And what the kinds of mechanisms are there that can bring it about. **What the collective pattern of settlement would be in terms of a segregated/integrated society?** Asking counterfactual question!
 - focus on each individual!
 - If we were to remove some important factors such as history, job location, etc. would it still be possible to generate similar outcomes?
 - An agent-based model allows us to test whether a set of conditions or parameters are sufficient to produce a certain outcome.
 - This project models the behavior of two types of agents in a neighborhood. The <orange> agents and <blue> agents get along with one another. But each agent wants to make sure that it lives near some of “its own.” The simulation shows how these individual preferences ripple through the neighborhood, leading to large-scale patterns. 
 
### EX_2. Simple Contagion Network Model
What happens to the structure of this network? Starting from a Lattice(hardware 1D or 2D..) Network, **What happens in something (such as a rumor) is spreading on the network** as we rewire "short distance edges" to make them "long distance edges" (introducing "Random ties" to "Lattice ties" - Tying between nodes that does not share neighbors - Combining Lattice_Nwk + Random_Nwk)? It increases the speed of diffusion because the **`"long distance ties"`** provide **short-cuts** that reduce the average path length of a network! So the world get smaller and the diffusion get faster because of the short cuts.
<img src="https://user-images.githubusercontent.com/31917400/70138652-9cc8f380-1688-11ea-8163-9bb1b86ec8b4.jpg" />

What drives diffusion? The network science thinks about how the **structure of interactions** affects that `diffusion process`. How information and behavior can spread through system? The **theories of "virality"** focuses on the `quality of the idea or item` to be diffused as an explanation for why some contagions spread and why others don’t. In contrast, the network model gives an idea that **`variations`, the pattern of who-is-connected-to-whom** can explain why some contagions succeed while others fail. How can we operationalize it in a systematical way? The network science starts from **"graph theory"**(node and edge) which focuses on `ties`(edge) and `vertex`(individual node) between people. We trace the series of steps the thing takes and spread over the network. 
 - rumor, brain, transportation network, etc.
 - Spreading is governed by the shape of the network!!
 - voting activities can be an example of a thing that spreads through networks because people’s likelihood of participating increases as more of their `peers` participate and participation is determined not only by psychological dispositions, but by `peer` influences.

> ### Simple Types of Network
 - __Lattice Graph(Spatial Network)__ physical network?
   <img src="https://user-images.githubusercontent.com/31917400/70074574-e2d37800-15f2-11ea-972b-4da5f12a4855.jpg" />
   
   - 1D Lattice cares immediate adjacency(right next door) or something farther(more doors down).  
   - 2D Lattice cares 8 entities(up,down,left,right + 4 corners).
   - `High Clustering` Coefficient
     - high clustering: two randomly selected contacts are likely to have a lot of same neighbors in common
 - __Random Graph__ trenscending network?
   <img src="https://user-images.githubusercontent.com/31917400/70075714-3e066a00-15f5-11ea-8727-9ace6917af5b.jpg" />
   
   - Low Path Length(AVG)
     - In Lattice, if you randomly select two nodes that are far apart from each other, it will require a lot of hops across each edge in order to connect(message) one node to another node. In Random Graph, the average path length between two randomly selected nodes is very small, taking only a few hops to get from any node to any other node in the network.
   - `Low Clustering` Coefficient
     - If you randomly select nodes, it is possible that none of them can be neighboring...

### EX_3. Complex Contagion Network Model
Unlike simple contagions (where a mere single contact is sufficient for transmissions), complex contagions may require **multiple sources of contact(repeated exposure)** before thing is transmitted. For example, the transmission(adaption) may require a sort of a **sense of proof** about the credibility of that thing. 
 - __Dynamics of Diffusion__
   - Contagion Threshold
     - A certain NO of contact(adaption by neighbors) is required to trigger transmission(adaption).
     <img src="https://user-images.githubusercontent.com/31917400/70147991-41edc700-169d-11ea-9170-148697938c73.jpg" />

   - Network structures & Types of Contagions to spread
     - __ASK:__ What `threshold rules` define a contagion that can spread in a system? what's the **largest threshold** that contagion could spread? **How many neighbors each node has and how many of them should show the adaption** so that contagion could spread? This might differ by the Graph structure.
     - We can measure this quantity of overlapping neighborhoods by using what's called a `clustering coefficient`. In general, networks with the **higher clustering coefficient** will be more effective at spreading contagions. 
       - > Lattice Graph - **Ring**
         <img src="https://user-images.githubusercontent.com/31917400/70173967-e71f9400-16cb-11ea-92b5-4bd12089f08b.jpg" />

         - Arranged on a ring, each node has the `same` number of neighbors. 
         - __0.5 Threshold:__ Each agent will adopt if `half` of their all neighbors have already adopted. 
           - `Seed Node` and the very **`Next Node` outside of the Seed Neighborhood** shares half of their neighbors. So node 1's neighborhood has adopted, node 4 is satisfied because half of their neighborhoods have adopted, thus node 4 will adopt the contagion. 
           -  We can see the pattern unfold because whenever a **given neighborhood has adopted**, the **`first node` outside that neighborhood** will always adopt!
           -  This will be true in the ring lattice no matter how many neighbors each node has.
           
       - > Lattice Graph - **Square**(Moore lattice)
         <img src="https://user-images.githubusercontent.com/31917400/70234521-b9ccf780-1758-11ea-82ea-e246d09308ce.jpg" />

         - Arranged on a grid, the nodes are connected to the neighbors to the "left|right|above|below|4 corners".  
         - One can see that the **`closest`** node to the **focal node** outside the seed neighborhood shares 3/8 of their neighbors with that **focal node**. And that means that from the outset, 3/8 of their neighbors have already adopted. 
         - This tells us that, at most, a threshold of `3/8` can spread in a square lattice. Any threshold with a contagion less than or equal to `3/8` will spread easily and the contagion cascades through the network. 
         - But the contagion with a threshold greater than `3/8` won't spread at all.
       - > Random Graph
         <img src="https://user-images.githubusercontent.com/31917400/70246964-77afb000-1770-11ea-923e-3274d927e2b4.jpg" />

         - Lattice have a very regular pattern where each node is connected to adjacent nodes, in Random Networks, nodes are just randomly connected. In very large Random Net, if zoom in on it and look at each neighborhood, one can see a **local tree-like property**. 
         - In Lattice, overlapping connections allowe complex contagions to spread easily because they provide for social reinforcement. In Random Net, since there are no overlapping neighborhoods/structures, and there's no opportunity for social reinforcement, **only simple contagions can spread**.
         - None of the nodes(agents) have overlapping neighbor????? The existence of `overlapping neighborhoods` is crucial to allow complex contagions to spread through a network.

> ### In the mixed network(Combining Lattice_Nwk + Random_Nwk), `Simple contagions` spread faster, but `Complex contagions` may not spread at all..
 - What if there's a distribution of thresholds? Or what if **thresholds are probabilistic** so people can change their decisions over time? 
 - Moreover, instead of just looking at networks where everyone has the same number of ties and ties are rewired, what if **there are hubs** in the network? 
 - Some nodes are extremely well connected and other have only a few ties. What if ties have different density? 
 
> ### How would all of these differences affect the dynamics? 
 - It turns out that the **threshold heterogeneity** actually makes the results stronger. 
 - It turns out that the **hub** actually makes it harder to spread **complex contagions**. 
 - It turns out adding more ties to the network, for much of the same reason as hubs, also make it harder to spread **complex contagions**.

### EX_4. Innovation Network Model
> Q. What's the best "communication network" structure to promote innovation?

In **Genetic Evolution**, every new organism is very similar to its parents, with only a few small changes known as mutations. What is important about the process is that a mutation never changes an entirely organism at once. Rather, it works with the machinery that already exists and just changes one or two things at a time(it's not feasible to change every feature at once).  

**NK space model** is for complex problem solving, inspired by evolutionary models of genetic combination.
 - The N in the NK space refers to the `number of features`.
 - The K in the NK space refers to the `level of interdependency` and `counts` how many other features each feature **interacts with**.
   - When k = 1, every feature interacts only with itself and every feature is therefore independent.
     - Change one feature at a time.
     - If the change improves the design, then keep it.
     - Otherwise, revert to old design.
   - When K > 1, ...damn difficult. In many cases, features are not independent....if you change one feature, that can impact how all the other features function(This interdependence between features is why complex problem solving is hard). The only way to get any further improvement after you've reach this point would be to `change many features at once`. In other words, we would need to jump to an entirely different part of the solution landscape in order to find anything better. But making big changes, `changing a lot of features at once, is really risky`. 
<img src="https://user-images.githubusercontent.com/31917400/70630254-34978600-1c23-11ea-9dff-b6fe7425cb16.jpg" />

> ### Try Agent Based Model!










































































