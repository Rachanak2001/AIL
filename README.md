# AIL

https://github.com/mandar196/Hate_Speech_Detection-NLP

https://github.com/eftekhar-hossain/CUET_NLP-EACL_2021

https://github.com/roshancyriacmathew/hate-speech-detection-using-machine-learning

https://github.com/hate-alert/IndicAbusive


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
**Tic-tac-toe**
#Tic-Tac-Toe Program using random number in Python

#importing all necessary libraries
import numpy as np
import random
from time import sleep

# Creates an empty board


def create_board():
    return(np.array([[0, 0, 0],
                     [0, 0, 0],
                     [0, 0, 0]]))

#Check for empty places on board


def possibilities(board):
    l = []
    for i in range(len(board)):
        for j in range(len(board)):
            if board[i][j] == 0:
                l.append((i, j))
    return(l)

#Select a random place for the player


def random_place(board, player):
    selection = possibilities(board)
    current_loc = random.choice(selection)
    board[current_loc] = player
    return(board)

#Checks whether the player has three
#of their marks in a horizontal row


def row_win(board, player):
    for x in range(len(board)):
        win = True
        for y in range(len(board)):
            if board[x, y] != player:
                win = False
                continue
        if win == True:
            return(win)
    return(win)

#Checks whether the player has three
#of their marks in a vertical row


def col_win(board, player):
    for x in range(len(board)):
        win = True
        for y in range(len(board)):
            if board[y][x] != player:
                win = False
                continue
        if win == True:
            return(win)
    return(win)

#Checks whether the player has three
#of their marks in a diagonal row


def diag_win(board, player):
    win = True
    y = 0
    for x in range(len(board)):
        if board[x, x] != player:
            win = False
    if win:
        return win
    win = True
    if win:
        for x in range(len(board)):
            y = len(board) - 1 - x
            if board[x, y] != player:
                win = False
            return win

#Evaluates whether there is
#a winner or a tie


def evaluate(board):
    winner = 0
    for player in [1, 2]:
        if (row_win(board, player) or
                col_win(board, player) or
                diag_win(board, player)):
            winner = player
    if np.all(board != 0) and winner == 0:
        winner = -1
    return winner

#Main function to start the game


def play_game():
    board, winner, counter = create_board(), 0, 1
    print(board)
    sleep(2)

    while winner == 0:
        for player in [1, 2]:
            board = random_place(board, player)
            print("Board after " + str(counter) + " move")
            print(board)
            sleep(2)
            counter += 1
            winner = evaluate(board)
            if winner != 0:
                break
    return(winner)
#Driver Code
print("Winner is: " + str(play_game()))

**OUTPUT**
[[0 0 0]
 [0 0 0]
 [0 0 0]]
Board after 1 move
[[0 0 0]
 [0 0 0]
 [0 1 0]]
Board after 2 move
[[0 2 0]
 [0 0 0]
 [0 1 0]]
Board after 3 move
[[0 2 0]
 [0 1 0]
 [0 1 0]]
Board after 4 move
[[2 2 0]
 [0 1 0]
 [0 1 0]]
Board after 5 move
[[2 2 0]
 [1 1 0]
 [0 1 0]]
Board after 6 move
[[2 2 0]
 [1 1 0]
 [0 1 2]]
Board after 7 move
[[2 2 1]
 [1 1 0]
 [0 1 2]]
Winner is: 1
