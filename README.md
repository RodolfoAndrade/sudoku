# Machine Learning Sudoku Solver

This is my approach to solve sudoku games using machine learning.

The dataset used: https://www.kaggle.com/bryanpark/sudoku

### Prerequisites
numpy               1.15.4
pandas              0.23.4
Keras               2.2.4
matplotlib          3.0.1

I have studied a little bit of machine learning and since i love playing Sudoku I tried to used both of these skills in this project. :D

My first approach was to use a simple Neural Network. In sudoku_nn I create just a simple fully connected layer in the same size of a sudoku game (9x9=81).
this only resulted in 80% accuracy. Which it is unforgiving, because sudoku is a simple game with some simple rules. It should be ease for a simple artificial intelligence learn the rules and solve it. The NN got wrong even the most obvious square. Which means it didn't learn the rules.

the dataset has one milions sudoku games. each one is a string of 81 char, for both of the quiz and the solution. the quiz has char 0 while the solution don't. 0 represent the empty cell. the cell which we mant to solve.
some games has 40 to 50 empty spaces. there is no ranking of dificulty.

knowing the dataset and the neural networking, i believe it wasnt able to reach 100% accuracy because sudoku game require some steps.
using elimination is possible to find the solution for some squares but for other it is required you to solve some other squares first.
so the sudoku problem demand a step-by-step solution. with my nn solution that tries to solve it in one go that didnt work.

to overcome that problem i thought the best solution would be multilayer perceptron, but i was mistaken. the accuracy increased to 80%.

finally the best solution was using lstm layer. it returned 99% accuracy.

