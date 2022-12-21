# AIL

https://github.com/mandar196/Hate_Speech_Detection-NLP

https://github.com/eftekhar-hossain/CUET_NLP-EACL_2021

https://github.com/roshancyriacmathew/hate-speech-detection-using-machine-learning

https://github.com/hate-alert/IndicAbusive


**Best first search**
from queue import PriorityQueue 
import matplotlib.pyplot as plt 
import networkx as nx 
# for implementing BFS | returns path having lowest cost
def best_first_search(source, target, n): 
    visited = [0] * n 
    visited[source] = True 
    pq = PriorityQueue() 
    pq.put((0, source)) 
    while pq.empty() == False: 
        u = pq.get()[1] 
        print(u, end=" ") # the path having lowest cost 
        if u == target: 
            break 
        for v, c in graph[u]: 
                if visited[v] == False: 
                    visited[v] = True 
                    pq.put((c, v)) 
                    #print() 
# for adding edges to graph 
def addedge(x, y, cost): 
    graph[x].append((y, cost)) 
    graph[y].append((x, cost))

v = int(input("Enter the number of nodes: "))
graph = [[] for i in range(v)] # undirected Graph 
e = int(input("Enter the number of edges: ")) 
print("Enter the edges along with their weights:")
for i in range(e): 
    x, y, z = list(map(int, input().split())) 
    addedge(x, y, z) 
source = int(input("Enter the Source Node: "))
target = int(input("Enter the Target/Destination Node: ")) 
print("\nPath: ", end = "") 
best_first_search(source, target, v) 

**OUTPUT**
