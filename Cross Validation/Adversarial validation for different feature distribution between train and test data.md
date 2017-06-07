# Adversarial validation
　　**Time-series** (or other intrinsically ordered data) can be problematic for cross-validation.
The usual approaches don't work, obviously regular cross validation is a bad idea **due to the time dimension**</br>

　　The general idea is to **check the degree of similarity between training and tests in terms of feature distribution**: 
if they are difficult to distinguish, the distribution is probably similar and the usual validation techniques should work. 
It does not seem to be the case, so we can suspect they are quite different. </br>

　　This intuition can be quantified by combining train and test sets, assigning 0/1 labels (0 - train, 1-test) and 
evaluating a binary classification task.</br>

　　Specifically, we’ll run the distinguishing classifier in cross-validation mode, to get predictions for all training examples. 
Then we’ll **see which training examples are misclassified as test and use them for validation.**</br>

　　To be more precise, we’ll choose a number of misclassified examples that the model was most certain about. It means that 
they look like test examples but in reality are training examples.</br>

1. Train a classifier to identify whether data comes from the train or test set.
2. Sort the training data by it’s probability of being in the test set.
3. Select the training data most similar to the test data as your validation set.

原文链接：[Adversarial validation](http://fastml.com/adversarial-validation-part-two/)
