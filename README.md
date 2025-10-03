<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:D.Vishwa       </h3>
<h3>Register Number:2305001034          </h3>
<H3>Aim:</H3>
<p>To Implement A * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm

a) Create a priority queue and insert the start node with distance 0.

b) Set the distance to the start node as 0 and to all other nodes as infinity.

c) While the queue is not empty:

   i) Remove the node with the smallest distance.

   ii) For each neighbor of this node:

   iii) Calculate the new tentative distance.

   iv) If the new distance is less, update it and push the neighbor into the queue.

   v) If the goal is reached, terminate.

d)The shortest distance to each node is now found.

## PROGRAM
```python

import heapq

def a_star(graph, heuristics, start, goal):

    queue = []
    heapq.heappush(queue, (heuristics[start], start, 0, [start]))

    visited = set()

    while queue:
        f_score, current, g_score, path = heapq.heappop(queue)

        if current == goal:
            print("Shortest Path:", path)
            print("Total Cost:", g_score)
            return path

        if current in visited:
            continue

        visited.add(current)

        for neighbor, weight in graph.get(current, []):
            if neighbor not in visited:
                new_g = g_score + weight
                new_f = new_g + heuristics[neighbor]
                heapq.heappush(queue, (new_f, neighbor, new_g, path + [neighbor]))

    print("No Path Found")
    return None

graph = {
    'A': [('B', 6), ('F', 3)],
    'B': [('A', 6), ('C', 3), ('D', 2)],
    'C': [('B', 3), ('E', 5), ('D', 1)],
    'D': [('B', 2), ('C', 1), ('E', 8)],
    'E': [('C', 5), ('D', 8), ('J', 5), ('I', 5)],
    'F': [('A', 3), ('G', 1), ('H', 7)],
    'G': [('F', 1), ('I', 3)],
    'H': [('F', 7), ('I', 2)],
    'I': [('G', 3), ('H', 2), ('E', 5), ('J', 3)],
    'J': [('E', 5), ('I', 3)],
}


heuristics = {
    'A': 10,
    'B': 8,
    'C': 5,
    'D': 7,
    'E': 3,
    'F': 6,
    'G': 5,
    'H': 3,
    'I': 1,
    'J': 3
}


a_star(graph, heuristics, 'A', 'H')

```

SAMPLE GRAPH I
![277151990-b1377c3f-011a-4c0f-a843-516842ae056a](https://github.com/user-attachments/assets/bedfaca4-a69a-468a-957d-a3def3f28836)

SAMPLE INPUT
10 14 <br>
A B 6 <br>
A F 3 <br>
B D 2 <br>
B C 3 <br>
C D 1 <br>
C E 5 <br>
D E 8 <br>
E I 5 <br>
E J 5 <br>
F G 1 <br>
G I 3 <br>
I J 3 <br>
F H 7 <br>
I H 2 <br>
A 10 <br>
B 8 <br>
C 5 <br>
D 7 <br>
E 3 <br>
F 6 <br>
G 5 <br>
H 3 <br>
I 1 <br>
J 0 <br>
<hr>
Sample Output

<img width="496" height="83" alt="image" src="https://github.com/user-attachments/assets/4a20129f-c48b-42e6-a5bd-bc4dfc5921f1" />





<hr>
<h2>Sample Graph II</h2>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/acbb09cb-ed39-48e5-a59b-2f8d61b978a3)


<hr>
<h2>Sample Input</h2>
<hr>
6 6 <br>
A B 2 <br>
B C 1 <br>
A E 3 <br>
B G 9 <br>
E D 6 <br>
D G 1 <br>
A 11 <br>
B 6 <br>
C 99 <br>
E 7 <br>
D 1 <br>
G 0 <br>
<hr>

SAMPLE OUTPUT

<img width="506" height="85" alt="image" src="https://github.com/user-attachments/assets/186e95c9-14e0-4175-887b-c31eb53731c7" />


## RESULT

 A * Search algorithm for a Graph using Python was implemented and executed successfully.
