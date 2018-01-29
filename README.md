# Optimal Feedback
This is a small project that aims to learn the optimal feedback matrices for backpropagating errors in fully-connected networks. This project was initially motivated by [this paper](https://www.nature.com/articles/ncomms13276), which showed that backpropagation works with random feedback weights, i.e. feedback weights do not have to be transposes of the forward weights, as is the case in the standard backpropagation algorithm. However, it is unlikely that iid random feedback weights would be optimal for backpropagating the errors; hence the aim of this project.  



