# Implementing Decision Trees from scratch

## Decision Trees and Intuition
1. Similar to how humans think, good way to start building intuition is DT are similar to 20 questions
2. Biggest advantage is the interpretability due to this there has been research to build Neural networks and then DT that trains on the neural network to get similar results and also give the benifit of interpretability which neural networks do not have
3. There are 2 main things to consider
    - splitting variable 'j'
    - splitting point 's'
4. GOAL 1 : to choose questions that help divide the data into homogeneous subsets
5. Regression Trees is an implementation where each each region is given a constant value generally the avg of the data in the node
6. Impurity of a node is defined by the gini index or entropy of the node this will also help us get an optimised splitting point.
7. A greedy approach is taken to find the splitting point 
8. We define a splitting point, then we have an objective function to minimise
    - In Regression Trees we want to min the min sum of squared error of the children
        - for each j pick s and pick the best s 
        - how to find best s ? we can iterate through the x values as those are the only possible split points
    - In classification we find the probability of each class occuring in the node and define the region as that class
        - we want to minimise the missclassificatio error which is how many points dont have the label defined by the class
        - we use gini index or entropy as the objective function, as they give us impurity and we want to minimise this. 

9. how to stop overfitting? when to stop ? 
    - there are several methods that help us decide when to stop
        - Early stopping ( if improvement in error is not significant then we stop)
        - leaf size can be defined 
        - reduced Error Pruning (create the entire tree then find a subtree with similar perfomance but also smaller)
        - cost complexity pruning ( this is like regularization we add a cost function which is the size of the tree(number of leaves))
            - we create the tree then one by one remove nodes 
                - Ca(T) = prediction error + a(T)
                    - T is subtree
                    - a controls the size of the tree
                        - larger a smaller tree vice versa

    - In classification when the difference in entropy of the parent with the weighted avg of the entropy of the children is large we split.
