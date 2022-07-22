Decission tree:

supervised learning

suitable for both classfication and regression

top-down

greedy: at each step of the tree-building process, the best split is made at
that particular step, rather than looking ahead and picking a split that will lead to a
better tree in some future step.

Model Flexibility: A smaller tree with fewer splits (that is, fewer regions
R1,...,RJ ) might lead to lower variance and better interpretation at the cost of a
little bias.

Cost complexity pruning – also known as weakest link pruning – is used to do this

grow a very large tree T0, and then prune it back in order to
obtain a subtree

### Summary 

1. Use recursive binary splitting to grow a large tree on the training data, stopping only
when each terminal node has fewer than some minimum number of observations.
2. Apply cost complexity pruning to the large tree in order to obtain a sequence of
best subtrees, as a function of α.
3. Use K-fold cross-validation to choose α. For each k = 1,...,K
3.1 Repeat Steps 1 and 2 on the (K −1)/Kth fraction of the training data, excluding the
kth fold.
3.2 Evaluate the mean squared prediction error on the data in the left-out kth fold, as a
function of α. Average the results, and pick α to minimize the average error.
4. Return the subtree from Step 2 that corresponds to the chosen value of α.


For a classification tree, we predict that each observation belongs to the most
commonly occurring class of training observations in the region to which it belongs.

criterion for making the binary splits:

regression: RSS
classification: classification error rate (the fraction of the training observations in that region that do not belong to the most common class) ->  not sufficiently sensitive -> prefer Gini index or Deviance

- Gini index: a measure of node purity – a small
value indicates that a node contains predominantly observations from a single class. an alternative is cross-entropy

In overall, trees are easy to expalin; generally poor predictive performance (predictive accuracy) as some of the other approaches.

## How to improve the predictive performance of trees

### Bagging (Bootstrap aggregation)
taking repeated samples from the (single) training
data set

generate B bootstrapped training set, recording the value / classpredicted by each of the B trees. regression -> average, classfication -> majority vote

Out-of-Bag Error:

leaving out observations that are sampled in the bootstrapped training dataset (out-of-bag) and can be used as test data.

On average, each bagged tree makes use of around two-thirds of the
observations.

# Question

6.1, P19, Top Left: A partition of two-dimensional feature space that could not result from
recursive binary splitting. Why?

6.1, P24,  The process described above may produce good predictions on the training set, but
is likely to overfit the data, leading to poor test set performance. Why?

6.1 P38, how to calculate Gini index?

6.1 P41, what is this slide talking about?

