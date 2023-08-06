# Alpha-Beta-Pruning
The alpha-beta pruning algorithm optimizes the minimax algorithm by eliminating irrelevant branches in a game tree, enhancing efficiency in decision-making.

## Introduction
Alpha-beta pruning is a search algorithm used in game trees to optimize the Minimax algorithm's evaluation process. It significantly reduces the number of nodes evaluated in the game tree, leading to faster and more efficient decision-making. The basic idea behind alpha-beta pruning is to eliminate branches of the game tree that are guaranteed to not affect the final decision, without actually evaluating all possible moves.

Here's a detailed step-by-step explanation of how alpha-beta pruning works:

1. **Minimax Algorithm Background:**
   The alpha-beta pruning algorithm builds upon the Minimax algorithm, which is used to find the best possible move for a player in a two-player zero-sum game (such as chess or tic-tac-toe). The Minimax algorithm explores the game tree recursively, considering both player's moves and opponent's moves, assigning values to each possible outcome (terminal states).

2. **Alpha and Beta Values:**
   In the context of alpha-beta pruning, two values, alpha and beta, are used to keep track of the best moves available to the maximizing player (usually referred to as the "maximizer") and the minimizing player (usually referred to as the "minimizer"), respectively.

3. **The Search Process:**
   The alpha-beta pruning algorithm starts at the root of the game tree and explores the branches by recursively evaluating nodes. At each node, the algorithm updates the alpha and beta values based on the following rules:

   - **Alpha Update (Maximizer's Perspective):** The maximizer's alpha value represents the best possible score they can achieve so far. When evaluating a child node, if the obtained value is greater than the current alpha value, the alpha value is updated to the new value.

   - **Beta Update (Minimizer's Perspective):** The minimizer's beta value represents the best possible score they can achieve so far. When evaluating a child node, if the obtained value is less than the current beta value, the beta value is updated to the new value.

4. **Pruning Condition:**
   During the search, the algorithm prunes (skips evaluating) certain branches of the game tree based on the following conditions:

   - If the beta value becomes less than or equal to the alpha value at any node, it means that the opponent (either maximizer or minimizer) would never choose this branch, as it doesn't lead to a favorable outcome for them. Hence, further exploration of this branch can be skipped.

5. **Applying Alpha-Beta Pruning:**
   The algorithm effectively prunes away subtrees that are guaranteed to be worse than the current best outcome. By avoiding the evaluation of irrelevant branches, the algorithm reduces the computational effort required to determine the optimal move.

6. **Terminal State Evaluation:**
   At terminal states (end of the game or a certain depth limit), the algorithm assigns utility values to the nodes representing the outcome of the game.

7. **Backpropagation:**
   As the algorithm completes the evaluation of child nodes and updates the alpha and beta values, the updated values are propagated back up the tree to help make decisions at higher levels.

By utilizing alpha-beta pruning, the algorithm significantly reduces the number of nodes evaluated in the game tree, focusing only on the most promising branches. This optimization allows the algorithm to search deeper into the tree within the same amount of time, resulting in more informed and efficient decision-making for the player.

## Problem Scenario
This is 2082. Robots have taken over the world. The International Robot Sports Committee  (IRSC) has been arranging Olympics for recreations of fellow robots for the last 10 years. In  Robot Olympic 2082, there is a game called ‘ROBO Sword-Fight’. In this game, two robots fight  against each other using swords.  
One of the participants in the ROBO Sword-Fight is Optimus Prime. Optimus Prime convincingly  won each of his previous games. There is only one game left for him to reach glory, and he will  have to fight Megatron in that game. In order to win the game, Optimus Prime will have to  achieve a certain amount of points. 

You have to perform the two tasks given below by using Alpha-Beta pruning. 
Task 1: Calculate the points and find if Optimus Prime won or not. [6] 
Task 2: Shuffle the generated list by S times and find how many times  Optimus Prime won. [4] 

[Hint: This will be a 4-level binary tree. On Level 0(MAX), it will be Optimus Prime’s Turn. On  Level 1(MIN) it will be Megatron’s Turn. On Level 2(MAX), again it will be Optimus Prime’s Turn.  On Level 3, there will be Terminal Nodes] 

NOTE: If any digit in your id is 0 consider it as 8
—--------------------------------------------------------------------------------------------------------Sample Input 1 : 
Enter your student ID 
25485465
Sample Output 1(For Task-1): 
Generated 8 random points between the minimum and maximum point limits:  [66, 74, 14, 73, 19, 26, 32, 40] 
Total points to win: 56 
Achieved point by applying alpha-beta pruning = 73 
The winner is Optimus Prime 
[How to find the winner: As the achieved point by Optimus Prime is 73 which is greater than 56, Optimus Prime wins. If the Achieved point by applying alpha-beta pruning >= Total points to win, then Winner is Optimus Prime. Otherwise, the Winner is Megatron] 
Sample Output 1(For Task-2): 
After the shuffle: 
List of all points values from each shuffles: [66, 73, 66, 73, 73, 66, 40, 66] The maximum value of all shuffles: 73 
Won 7 times out of 8 number of shuffles 
Explanation: 
25485465 = 5 
( 5th digit of your student ID)	Minimum points the Optimus Prime can  achieve from the game is 5
25485465 = 56*1.5 = 84 
( Reverse last 2 digits of your student ID and  multiply that number with 1.5 and take  nearest integer (upper))	1. Maximum points the Optimus  
Prime can achieve from the game  = 84 
2. Total points to win = 56 
(reverse of last two digits of the ID)

25485465 = 8
(4th digit of your student ID)	Total number of shuffles, S = 8 (for Task-2)
—---------------------------------------------------------------------------------------------------------
Sample Input 2 : 
Enter your student ID 
17564039
Sample Output 2:  
Generated 8 random points between the minimum and maximum point limits:  [36, 26, 112, 57, 85, 80, 107, 28] 
Total points to win: 93 
Achieved point by applying alpha-beta pruning = 85 
The Winner is Megatron 
After the shuffle: 
List of all points values from each shuffle: [107, 80, 85, 80, 85, 107] 
The maximum value of all shuffles: 107 
Won 2 times out of 6 number of shuffles 

## Code explanation
The code simulates a game scenario using the alpha-beta pruning algorithm. Let's break down the code and its functionality:

1. **Function Definitions:**
    - `alpha_beta_pruning`: This function implements the alpha-beta pruning algorithm. It takes as input a game node, the current depth in the game tree, alpha and beta values for pruning, and a boolean indicating whether the player is maximizing. It recursively evaluates the game tree nodes while optimizing with alpha-beta pruning.
    - `calculate_points`: A simple function that returns the points associated with a given game node.
    - `is_terminal_node`: A function that checks whether a given node is a terminal node in the game tree.
    - `generate_children`: A function that generates child nodes for a given game node.
    - `optimus_prime_turn`: A function that initiates Optimus Prime's turn using the alpha-beta pruning algorithm.

2. **Class Definition:**
    - `Node`: This class defines a game node, containing points, children nodes, and a flag indicating whether it's a terminal node.

3. **`task1` Function:**
    This function uses the student's ID to perform a simulation of the game with certain parameters. It generates random points within specified limits and initiates Optimus Prime's turn using alpha-beta pruning to achieve a certain goal. It then determines the winner based on the achieved points and the total points needed to win.

4. **`task2` Function:**
    This function simulates shuffling the results list (representing Optimus Prime's wins and losses) a specified number of times. It counts how many times Optimus Prime wins after each shuffle and reports the total number of wins out of the specified shuffle times.

5. **Main Section (`__main__`):**
    - The script begins by prompting the user to input their student ID.
    - It then calls `task1` and `task2` functions to execute the game simulation based on the provided student ID.

The script essentially simulates a game scenario where Optimus Prime and Megatron are players, and the alpha-beta pruning algorithm is used to determine the best moves. Task 1 simulates a single game scenario and declares the winner, while Task 2 performs multiple simulations by shuffling the results list to determine the percentage of wins for Optimus Prime out of a specified number of shuffles.

## Conclusion
In conclusion, the alpha-beta pruning algorithm stands as a remarkable enhancement to the Minimax algorithm, revolutionizing decision-making processes in game-playing scenarios. By intelligently pruning irrelevant branches in the game tree, alpha-beta pruning significantly reduces the computational burden without compromising the quality of decisions. This efficiency gain allows for deeper exploration of possible moves within the same time frame, leading to more informed choices and optimal outcomes. Alpha-beta pruning's ingenious exploitation of the properties of asymmetric games, where player strategies are often imbalanced, cements its status as a fundamental optimization technique in artificial intelligence and game theory, contributing to the advancement of strategic reasoning and decision-making in various applications, ranging from classic board games to complex strategic planning.
