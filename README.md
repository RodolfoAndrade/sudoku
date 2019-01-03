# Machine Learning Sudoku Solver



Sudoku is a game with 3x3 blocks of 9x9 numbers or empty space. The goal is to fill the empty space following the rules. Every number must be unique in the line, column and block it is located. The possible numbers is in the range of 1 to 9. 

This is my approach to solve sudoku games using machine learning. First, I used a simple Neural network, then a Multilayer Neural network. But the solution was only found using a Long Short-Term Memory network.



The dataset used can be found in this link: https://www.kaggle.com/bryanpark/sudoku



## Getting Started



to run these notebooks on your computer you have to install anaconda or miniconda with python 3.7. after installation please follow the tutorials to create an environment and install the prerequisites.



## Prerequisites

numpy        1.15.4


pandas        0.23.4


Keras        2.2.4


matplotlib    3.0.1



## more information



I have studied a little bit of machine learning, and since I like playing Sudoku, I tried to use both of these skills in this project. :D



My first approach was to use a simple Neural Network (NN). In the sudoku_nn file, I create a simple fully connected layer in the same size as a sudoku game (9x9=81). 
Which resulted in 80% accuracy. 
Which it is unforgiving because sudoku is a simple game with some simple rules. It should be easy for a simple artificial intelligence learn the rules and solve it. 
The NN got wrong even the most obvious square. Which means it didn't learn the rules.



The dataset has one million sudoku games. Each one is a string of 81 char, for both the quiz and the solution. The quiz has char 0, while the solution doesn't. 0 represent the empty cell, the cell which we want to solve.

Some games have 40 to 50 empty spaces. There is no difficulty ranking.



Knowing the dataset and the neural network, I believe it wasn't able to reach 100% accuracy because sudoku game requires steps to find all the empty cells. 
By seeing the line, column and square of an empty cell is possible to exclude some numbers from the possibilities. Using this elimination is possible to find only one possible number as the solution for some cells, but for others, it is required that you solve some other cells first.

So the sudoku problem demands a step-by-step solution. So my NN solution that tries to solve it in one go didn't work.



To overcome that problem I thought the best solution would be to use a multilayer perceptron (MLP), but I was mistaken. The accuracy didn't go further than 77%.



Finally, the best solution was using LSTM. This algorithm uses a temporal, step-by-step solution. 
For that, I had to create a new dataset from the old one. I programmed an algorithm (located in the sudoku_algorithm file) that solves each sudoku game. This simple algorithm followed the rules to find the cell which got only one possible number and saves it in the game. Then, the algorithm is executed again until there are no empty cells. With this, I was capable of creating a dataset with the steps to solve each game. Some games were solved using 4-7 steps, so I round it up to 10 steps to create a homogeneous dataset. 
Later I created a simple LSTM network that returned 99% accuracy. :D