# AIL

https://github.com/mandar196/Hate_Speech_Detection-NLP

https://github.com/eftekhar-hossain/CUET_NLP-EACL_2021

https://github.com/roshancyriacmathew/hate-speech-detection-using-machine-learning

https://github.com/hate-alert/IndicAbusive

https://github.com/vidhur2k/Multilngual-Hate-Speech

https://www.startertutorials.com/blog/digital-forensics-life-cycle.html

https://www.rcybersolutions.com/cybersecurity-real-life-cases-solved-by-digital-forensic-evidence/


**Best first search**<br>
from queue import PriorityQueue <br><br>
import matplotlib.pyplot as plt <br>
import networkx as nx <br>
#for implementing BFS | returns path having lowest cost<br>
def best_first_search(source, target, n): <br>
    visited = [0] * n <br>
    visited[source] = True <br>
    pq = PriorityQueue() <br>
    pq.put((0, source)) <br>
    while pq.empty() == False: <br>
        u = pq.get()[1] <br>
        print(u, end=" ") # the path having lowest cost <br>
        if u == target: <br>
            break <br>
        for v, c in graph[u]: <br>
                if visited[v] == False: <br>
                    visited[v] = True <br>
                    pq.put((c, v)) <br>
                    #print() <br>
#for adding edges to graph <br>
def addedge(x, y, cost): <br>
    graph[x].append((y, cost)) <br>
    graph[y].append((x, cost))<br>
<br>
v = int(input("Enter the number of nodes: "))<br>
graph = [[] for i in range(v)] # undirected Graph <br>
e = int(input("Enter the number of edges: ")) <br>
print("Enter the edges along with their weights:")<br>
for i in range(e): <br>
    x, y, z = list(map(int, input().split())) <br>
    addedge(x, y, z) <br>
source = int(input("Enter the Source Node: "))<br>
target = int(input("Enter the Target/Destination Node: ")) <br>
print("\nPath: ", end = "") <br>
best_first_search(source, target, v) <br>
<br>
**OUTPUT**<br>
Enter the number of nodes: 4<br>
Enter the number of edges: 5<br>
Enter the edges along with their weights:<br>
0 1 1<br>
0 2 1<br>
0 3 2<br>
2 3 2<br>
1 3 3<br>
Enter the Source Node: 2<br>
Enter the Target/Destination Node: 1<br>
<br>
Path: 2 0 1 <br>
<br>
**Tic-tac-toe**<br>
#Tic-Tac-Toe Program using random number in Python<br>
<br>
#importing all necessary libraries<br>
import numpy as np<br>
import random<br>
from time import sleep<br>
<br>
#Creates an empty board<br>
<br>

def create_board():<br>
    return(np.array([[0, 0, 0],<br>
                     [0, 0, 0],<br>
                     [0, 0, 0]]))<br>
<br>
#Check for empty places on board<br>
<br>

def possibilities(board):<br>
    l = []<br>
    for i in range(len(board)):<br>
        for j in range(len(board)):<br>
            if board[i][j] == 0:<br>
                l.append((i, j))<br>
    return(l)<br>

#Select a random place for the player<br>

<br>
def random_place(board, player):<br>
    selection = possibilities(board)<br>
    current_loc = random.choice(selection)<br>
    board[current_loc] = player<br>
    return(board)<br>
<br>
#Checks whether the player has three<br>
#of their marks in a horizontal row<br>

<br>
def row_win(board, player):<br>
    for x in range(len(board)):<br>
        win = True<br>
        for y in range(len(board)):<br>
            if board[x, y] != player:<br>
                win = False<br>
                continue<br>
        if win == True:<br>
            return(win)<br>
    return(win)<br>
<br>
#Checks whether the player has three<br>
#of their marks in a vertical row<br>

<br>
def col_win(board, player):<br>
    for x in range(len(board)):<br>
        win = True<br>
        for y in range(len(board)):<br>
            if board[y][x] != player:<br>
                win = False<br>
                continue<br>
        if win == True:<br>
            return(win)<br>
    return(win)<br>
<br>
#Checks whether the player has three<br>
#of their marks in a diagonal row<br>
<br>

def diag_win(board, player):<br>
    win = True<br>
    y = 0<br>
    for x in range(len(board)):<br>
        if board[x, x] != player:<br>
            win = False<br>
    if win:<br>
        return win<br>
    win = True<br>
    if win:<br>
        for x in range(len(board)):<br>
            y = len(board) - 1 - x<br>
            if board[x, y] != player:<br>
                win = False<br>
            return win<br>
<br>
#Evaluates whether there is<br>
#a winner or a tie<br>
<br>

def evaluate(board):<br>
    winner = 0<br>
    for player in [1, 2]:<br>
        if (row_win(board, player) or<br>
                col_win(board, player) or<br>
                diag_win(board, player)):<br>
            winner = player<br>
    if np.all(board != 0) and winner == 0:<br>
        winner = -1<br>
    return winner<br>
<br>
#Main function to start the game<br>

<br>
def play_game():<br>
    board, winner, counter = create_board(), 0, 1<br>
    print(board)<br>
    sleep(2)<br>
<br>
    while winner == 0:<br>
        for player in [1, 2]:<br>
            board = random_place(board, player)<br>
            print("Board after " + str(counter) + " move")<br>
            print(board)<br>
            sleep(2)<br>
            counter += 1<br>
            winner = evaluate(board)<br>
            if winner != 0:<br>
                break<br>
    return(winner)<br>
#Driver Code<br>
print("Winner is: " + str(play_game()))<br>
<br>
**OUTPUT**<br>
[[0 0 0]<br>
 [0 0 0]<br>
 [0 0 0]]<br>
Board after 1 move<br>
[[0 0 0]<br>
 [0 0 0]<br>
 [0 1 0]]<br>
Board after 2 move<br>
[[0 2 0]<br>
 [0 0 0]<br>
 [0 1 0]]<br>
Board after 3 move<br>
[[0 2 0]<br>
 [0 1 0]<br>
 [0 1 0]]<br>
Board after 4 move<br>
[[2 2 0]<br>
 [0 1 0]<br>
 [0 1 0]]<br>
Board after 5 move<br>
[[2 2 0]<br>
 [1 1 0]<br>
 [0 1 0]]<br>
Board after 6 move<br>
[[2 2 0]<br>
 [1 1 0]<br>
 [0 1 2]]<br>
Board after 7 move<br>
[[2 2 1]<br>
 [1 1 0]<br>
 [0 1 2]]<br>
Winner is: 1<br>
<br>
