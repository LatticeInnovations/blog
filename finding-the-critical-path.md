---
description: Soura Bhattacharyya | Apr 10, 2023
---

# Finding the critical path

## Motivation

One of the key analytical measures of a project is its critical path, or CP—the longest path from start to finish. Tasks on the CP have to be closely monitored; delays in the CP will delay the entire project.

In early 2023, we developed an in-house analytical tool that used dependency data to calculate critical path. At its heart lies the Bellman-Ford (BF) algorithm.&#x20;

This post applies the BF algorithm to the task of calculating the critical path, and provides specific scenarios that are not adequately addressed by most off-the-shelf project management software.&#x20;

## Introduction

We start with a project that has tasks with durations and dependencies (Fig 1). There are multiple paths from start `s` to finish `f`. The longest path is the critical path (CP), which governs the total project duration. Figure 1 shows that path `{s,k,h,i,m,n,f}`, totalling 15 days, is the CP.

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>Figure 1: task durations and connections</p></figcaption></figure>

Graph theory can be applied to analyze such a diagram. In graph theory, each task is called a _**vertex**_. Each dependency is called an _**edge**_.

Projects can be thought of _**weighted, directed, acyclic graphs**_, commonly abbreviated as weighted DAGs.  _**Weights**_ represent any numeric property of an edge; here, we use task duration. _**Directed**_ graphs are unidirectional—we move from predecessors to successors (from `s` to `a`), but not the other way. _**Acyclic**_ graphs do not have cycles, or loops.

To analyze projects, we assign weights equal to the task duration to each of the edges, so that path length converts to project duration. To find the CP, we need an algorithm that finds the longest path.\


## Assigning weights to edges

Before we find the longest path, we have to assign weights to edges. If we assign the duration of task `v` to the edge `{v,w}` that connects to the successor `w`, figure 1 transforms into figure 2.

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>Figure 2: Vertices and weighted edges</p></figcaption></figure>

Task `a` is 2 days long, and is followed by task `b`. Thus, we set edge length `C(a,b)` equal to the duration of task `a`. We could also calculate `C(a,b)` by the difference in start dates:

`startDiff = startDate(a)-startDate(b)`

While convenient, the start-date-difference method is flawed, because it includes any slack between `a` and `b` as a part of the path length. This defeats the purpose of finding the longest path.

However, startDiff is a useful parameter to optimize our calculations. Concretely,

1. If b is a task, then  `C(a,b) = min (startDiff(a,b), Duration(a))`&#x20;
2. If b is a milestone, then `C(a,b) = Duration(a)`

This formula accommodates cases where a task finishes on the same day as its successor. In such cases, the duration is one day, but `startDiff` is zero. It also accommodates milestones that are achieved as soon as a task ends, including the project end milestone.

### Example

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption><p>Figure 3: A sample gantt with four sequential tasks</p></figcaption></figure>

In the example above, only path is the critical path. It is 1 + 4 + 1 = 6 days long, including weekends/ holidays.

Holidays have been intentionally included. Once we calculate the project duration—7 calendar days—we can compare it to the critical path length of 6 calendar days, and infer that the critical path has one day of slack. As we can see, there is a day of slack between the third and fourth tasks.

## Bellman-Ford Algorithm

### Notation

Before we move to the algorithm, let us formalize notation:

`n` = number of vertices. In the context of a gantt, this is the number of tasks.

`m` = number of edges. In the context of a gantt, this is the number of dependencies.

`s` = source vertex, `f` = destination vertex (i.e. the starting and finishing tasks)

`v` = any vertex

`e` = any edge&#x20;

`L(i,v)` = minimum length of a path from s to v, where i represents the number of hops. `i ∈ {0, 1, 2, … n-1}`, because the longest possible path is one that touches all the vertices once.

`C(v,w)` = path length between two vertices connected by an edge, v and w

### Inverting weights

Bellman-Ford searches for the shortest path. However, we need to find the longest path — the critical path (CP). To “trick” the algorithm into finding the longest path, we invert the signs of all weights, so that a task of weight (duration) 2 days is represented as `-2`. As a result, the path with the highest negative value is selected as the shortest: the critical path.

### Outer loop

We iterate through an outer loop a maximum of n-1 times, because an acyclic (no loops) path can, at most, pass through each vertex once. And a path passing through all n vertices has n-1 segments, or hops. In our example, n=14, hence there are a maximum of 13 outer loop iterations. However, because our graphs are sparse — most vertices have one or two inbound edges — we usually need fewer iterations.

### Inner loop

Within each outer loop, we examine all available next steps, and “take the next step” wherever we find that it is a shorter path to a vertex. “Taking the next step” consists of 2 actions — updating the distance to the vertex, and adding the new vertex to the array that stores the path.

Hence, we execute the following inner loop:

| <p>for each edge (u, v) with weight w in edges do</p><p>    if distance[u] + w &#x3C; distance[v]    // is it faster to get to v via w?</p><p>    then</p><p>        distance[v] := distance[u] + w  // update distance[v]</p><p>        predecessor{s, … ,u} := {s, … u, v} // predecessor array updated</p><p>return distance, predecessor</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

### Base case, i=0

`i=0` means that there are zero segments, i.e. no hops—hence we can only get from s to s.&#x20;

Therefore, `L(0,s) = 0`, representing a path of zero length from the vertex to itself.

Also, we set `L(0,v) = ∞` for all other vertices, because we cannot reach any of them in zero hops. Instead of infinity, we can use a sufficiently large number, say 10,000, that is guaranteed to always be larger than any task’s duration (in days).

Thus, the distance array for the zeroth iteration is:

| iter | s | a | b | c | d | e | k | g | h | i | j | m | n | f |
| ---- | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 0    | 0 | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ |

\## Iteration 1, i=1

Previously computed vertices in red, vertices computed in this iteration in yellow, and unchanged vertices in blue.

| <p>paths and their lengths:</p><p>sk: L(1,k) = 0</p><p>sa: L(1,a) = 0</p> |
| ------------------------------------------------------------------------- |

\
\


distance array:

| iter | s | a | b | c | d | e | k | g | h | i | j | m | n | f |
| ---- | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| 1    | 0 | 0 | ∞ | ∞ | ∞ | ∞ | 0 | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ | ∞ |

\
Iteration 2

| <p>paths and path lengths:</p><p>skh: L(2,h) = -1</p><p>skg: L(2,g) = -1</p><p>sab: L(2,b) = -2</p> |
| --------------------------------------------------------------------------------------------------- |

\


| iter | s | a | b  | c | d | e | k | g  | h  | i | j | m | n | f |
| ---- | - | - | -- | - | - | - | - | -- | -- | - | - | - | - | - |
| 2    | 0 | 0 | -2 | ∞ | ∞ | ∞ | 0 | -1 | -1 | ∞ | ∞ | ∞ | ∞ | ∞ |

#### Iteration 3

| <p>paths and lengths:</p><p>skhi: -2</p><p>skgd: -1</p><p>sabc: -5</p><p>sabe: -5</p> |
| ------------------------------------------------------------------------------------- |

\
\
\
\
\
\


| iter | s | a | b  | c  | d  | e  | k | g  | h  | i  | j | m | n | f |
| ---- | - | - | -- | -- | -- | -- | - | -- | -- | -- | - | - | - | - |
| 3    | 0 | 0 | -2 | -5 | -2 | -5 | 0 | -1 | -1 | -2 | ∞ | ∞ | ∞ | ∞ |

\
\


#### Iteration 4

\


| <p>paths and lengths:</p><p>skhim: -5</p><p>skhij: -5</p><p>skgde: -3</p><p>sabcd: -7</p><p>sabef: -7</p> |
| --------------------------------------------------------------------------------------------------------- |

\
\
\
\
\


| iter | s | a | b  | c  | d  | e  | k | g  | h  | i  | j  | m  | n | f  |
| ---- | - | - | -- | -- | -- | -- | - | -- | -- | -- | -- | -- | - | -- |
| 4    | 0 | 0 | -2 | -5 | -7 | -8 | 0 | -1 | -1 | -2 | -5 | -5 | ∞ | -7 |

\


#### Iteration 5

\


| <p>paths and lengths:</p><p>skhimn: -12</p><p>skhijn: -12</p><p>skgdef: -5</p><p>sabcde: -8</p><p>sabef: -7 // no change, reached finish in prior iteration </p> |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
\


| iter | s | a | b  | c  | d  | e  | k | g  | h  | i  | j  | m  | n   | f  |
| ---- | - | - | -- | -- | -- | -- | - | -- | -- | -- | -- | -- | --- | -- |
| 5    | 0 | 0 | -2 | -5 | -7 | -8 | 0 | -1 | -1 | -2 | -5 | -5 | -12 | -7 |

\


#### Iteration 6

\


| <p>paths and path lengths:</p><p>skhimnf: -15</p><p>skhijnf: -10 // distance(f) not updated</p><p>skgdef: -5 // no change, reached finish</p><p>sabcdef: -9</p><p>sabef: -7 // no change, reached finish</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

\


Thus, the algorithm finds 5 paths from start to finish. The “shortest” path has the highest negative value of -15. Updates to the distance array can be summarized as follows:&#x20;

| iter | s | a | b  | c  | d  | e  | k | g  | h  | i  | j  | m  | n   | f   |
| ---- | - | - | -- | -- | -- | -- | - | -- | -- | -- | -- | -- | --- | --- |
| 0    | 0 | ∞ | ∞  | ∞  | ∞  | ∞  | ∞ | ∞  | ∞  | ∞  | ∞  | ∞  | ∞   | ∞   |
| 1    | 0 | 0 | ∞  | ∞  | ∞  | ∞  | 0 | ∞  | ∞  | ∞  | ∞  | ∞  | ∞   | ∞   |
| 2    | 0 | 0 | -2 | ∞  | ∞  | ∞  | 0 | -1 | -1 | ∞  | ∞  | ∞  | ∞   | ∞   |
| 3    | 0 | 0 | -2 | -5 | -2 | -5 | 0 | -1 | -1 | -2 | ∞  | ∞  | ∞   | ∞   |
| 4    | 0 | 0 | -2 | -5 | -7 | -8 | 0 | -1 | -1 | -2 | -5 | -5 | ∞   | -7  |
| 5    | 0 | 0 | -2 | -5 | -7 | -8 | 0 | -1 | -1 | -2 | -5 | -5 | -12 | -7  |
| 6    | 0 | 0 | -2 | -5 | -7 | -8 | 0 | -1 | -1 | -2 | -5 | -5 | -12 | -15 |

\


The algorithm terminates in iteration 6 because all paths have reached the finish point.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdxXDvg9XWakJm2UEyoXhFvzYUr2BMSG189yXZnxbqu4Uv7t3oOtl5KJyONrMYw99y0QoXdmjN3RwaCQ--eFYBfgV2b-TBYVwF0QtL2CZeRJLjD1Gap9GlWdhagTaRCDLNokamdCzYwFW6K1rvkTvi0Xev_?key=cW25FWwjex3hGYwWCYZCZg" alt=""><figcaption></figcaption></figure>

At the end of iteration 6, we also have all paths available as a set of arrays.

### Pseudocode

Source: [Wikipedia](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm)

| <p>function BellmanFord(list vertices, list edges, vertex source) is</p><p><br></p><p>    // This implementation takes in a graph, represented as</p><p>    // lists of vertices (represented as integers [0..n-1]) and edges,</p><p>    // and fills two arrays, distance and predecessor, holding</p><p>    // the shortest path from the source to each vertex</p><p><br></p><p>    distance := list of size n</p><p>    predecessor := list of size n</p><p><br></p><p>    // Step 1: initialize graph</p><p>    for each vertex v in vertices do</p><p>        distance[v] := inf     // Initialize distance to all vertices to ∞</p><p>        predecessor[v] := null // And having a null predecessor</p><p>    </p><p>    distance[source] := 0      // Distance from the source to itself is zero</p><p><br></p><p>    // Step 2: updated distance and predecessors repeatedly</p><p>    repeat V−1 times:          // V = number of vertices (tasks)</p><p>         for each edge (u, v) with weight w in edges do</p><p>             if distance[u] + w &#x3C; distance[v] </p><p>             then</p><p>                 distance[v] := distance[u] + w  // distance list updated</p><p>                 predecessor[v] := u    // predecessor list updated</p><p>    return distance, predecessor</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |



### Python implementation&#x20;

Source: [Programiz.com](https://www.programiz.com/dsa/bellman-ford-algorithm). Limitation: this implementation does not print the path

| <p>class Graph:</p><p>    def __init__(self, vertices):</p><p>        self.V = vertices   # Total number of vertices in the graph</p><p>        self.graph = []     # Array of edges</p><p><br></p><p>    # Add edges</p><p>    def add_edge(self, s, d, w):</p><p>        self.graph.append([s, d, w])</p><p><br></p><p>    # Print the solution</p><p>    def print_solution(self, dist):</p><p>        print("Vertex Distance from Source")</p><p>        for i in range(self.V):</p><p>            print("{0}\t\t{1}".format(i, dist[i]))</p><p><br></p><p>    def bellman_ford(self, src):</p><p><br></p><p>        # Step 1: fill the distance array and predecessor array</p><p>        dist = [float("Inf")] * self.V</p><p>        # Mark the source vertex</p><p>        dist[src] = 0</p><p><br></p><p>        # Step 2: relax edges |V| - 1 times</p><p>        for _ in range(self.V - 1):</p><p>            for s, d, w in self.graph:</p><p>                if dist[s] != float("Inf") and dist[s] + w &#x3C; dist[d]:</p><p>                    dist[d] = dist[s] + w</p><p><br></p><p>        # Print the distance and predecessor array</p><p>        self.print_solution(dist)</p> |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
This code can be [tried out directly](https://replit.com/@SouraBhattacha2/BellmanFordAlgo#main.py) on a browser-based IDE, with the following inputs:

| <p>g = Graph(5)</p><p>g.add_edge(0, 1, 5)</p><p>g.add_edge(0, 2, 4)</p><p>g.add_edge(1, 3, 3)</p><p>g.add_edge(2, 1, 6)</p><p>g.add_edge(3, 2, 2)</p><p><br></p><p>g.bellman_ford(0)</p> |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

\
The output is:

| <p>Vertex Distance from Source</p><p>0       0</p><p>1       5</p><p>2       4</p><p>3       8</p><p>4       inf</p> |
| -------------------------------------------------------------------------------------------------------------------- |

## Resources for self-study

* [Algorithms: Design and Analysis, Part 2 | edX](https://learning.edx.org/course/course-v1:StanfordOnline+SOE-YCSALGORITHMS2+1T2020/home) > The Bellman-Ford Algorithm: This is a Stanford undergraduate course, available for free on edX.
* [Algorithms, Part II | Coursera](https://in.coursera.org/learn/algorithms-part2#syllabus) > Shortest Paths: This is a Princeton undergraduate course, available for free on Coursera. It includes guidance for java implementation.
