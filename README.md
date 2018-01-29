# Optimal Feedback
This is a small project that aims to learn the optimal feedback matrices for backpropagating errors in fully-connected networks. This project was initially motivated by [this paper](https://www.nature.com/articles/ncomms13276), which showed that backpropagation works fine with random feedback weights (through a mechanism they called *feedback alignment*), i.e. feedback weights do not have to be transposes of the forward weights, as is the case in the standard backpropagation algorithm. However, it is unlikely that iid random feedback weights would be optimal for backpropagating the errors; hence the aim of this project. The following diagram illustrates the general approach: 

![optimal_feedback](https://user-images.githubusercontent.com/17934496/35534494-470b716a-0506-11e8-90db-ca8553f71d1f.png)

We unroll the updating of the forward weights, `W`, for `N` steps (simulating `N` steps of SGD, for example, although we also consider more sophisticated variants such as Adam) and "bake" it into the computation graph (black arrows). The feedback matrices, `B`, are then updated in a standard way by backpropagating the gradients through the entire computation graph (red arrows). We use Adam for updating `B`. Here are some questions we are interested in addressing with this setup:

* How do optimal feedback matrices differ from iid random matrices?
* How do the solutions change if we allow the feedback matrices to change during the `N` updates of the inner loop? Note that this is what happens in standard backprop, where at each step the feedback weights are transposes of the forward weights. 
* Do the learned feedback matrices generalize well across different `N`, i.e. if we train `B` for a small `N`, how well does it generalize to much larger `N`?

One definite advantage of this setup over random feedback alignment is that the model here has a well-defined objective function, e.g. total cost over `N` updates, so the dynamics can be understood as minimizing an objective function. Random feedback alignment, on the other hand, does not have an objective function, because the dynamics it describes is non-conservative, as noted by the authors.

I will share my code here, once I make sufficient progress on this project.

