Assignment 2: 2048
=========

Your task is to implement a game AI for the 2048 game based on expectimax search. The base game engine uses code from [here](https://gist.github.com/lewisjdeane/752eeba4635b479f8bb2). 

Due date
-----
April-26 5pm.  

Submission
----
You only need to submit the `ai.py` file on Gradescope for grading. 

If you have changed other files, make sure that your implementation works properly with the given `main.py` and `game.py`, and `test.py` which we will use for grading. 

You can change almost anything in the starter code in `ai.py` except the the `compute_decision` function at Line 85. This function will be used by the tests. 

Task
-----
Model the AI player as a max player, and the computer as a chance player (picking a random open spot to place a 2-tile), implement the expectimax algorithm to compute decisions for the AI player. 

You can play the game manually using the arrow keys. Pressing 'Enter' will let the AI play, and pressing 'Enter' again will stop the AI player.

Read the game engine code from 'game.py' and see how it returns the game state and evaluate its score from an arbitrary game state after an arbitrary player move. 

Explicitly construct a depth-3 game tree from any state of the game (like the tree from the slides). Depth-3 means the tree has the following levels: 

- root: player
- level 1: computer 
- level 2: player
- level 3: terminal with payoff (note that we say "terminal" to mean the leaf nodes in the shallow game tree, not the termination of the game itself)

This tree represents all the game states of a player-computer-player sequence (the player makes a move, the computer place a tile, and then the player makes another move, and then evaluate the score). 

Compute the expectimax values of all the nodes in the game tree, and return the optimal move for the player. In the starter code the AI just returns a random move.

If you have implemented this AI correctly, you depth-3 search should almost always reach 512 tiles and a score over 5000 quite often, as shown in the movie file. 

Testing
-----
The file 'test\_utils.py' contains code for testing that with the depth-3 tree and the expectimax algorithm, your AI returns the right directions and values on 3 test states. Run the tests using:

$ python main.py -t 1

For grading, we will run tests in the same way on other test states and see if your depth-3 tree and experimax values are computed correctly. 


Extra credits (3 points)
------
While depth-3 search gives okay performance, it can apparently be improved by searching more depth or improving the evaluation function, or both. For improving the evaluation function, you can implement a heuristic value that takes into account of the difference between a "good" and "bad" game state. You can feel free to use online resources to see what strategies people have been using in playing 2048. 

If you want to try this extra credits part, implement a stronger AI in the `compute_decision_ec` function at the bottom of the `ai.py` file. When running the game, pressing `e` will activate the decisions made by the `compute_decision_ec` function. 

You can get up to 3 extra points if you can engineer the AI to reach 2048 often (achieving a score of more than 20,000 on at least 4/10 runs), while each step does not take too long when running on a laptop. Note that if you implement a large tree, the search may make each decision so slow that you do not want to watch it play. In that case you want to think about how to improve the implementation. 

To test your extra credit implementation, run:

$ python main.py -t 2

In order to get the extra credits, you will need to achieve a score of more than 20,000 on at least 4/10 runs.

Notes
------
The following keyboard options are available:
    - 'r': restart the game
    - 'u': undo a move
    - '3'-'7': change board size
    - 'g': toggle grayscale

