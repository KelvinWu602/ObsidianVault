#machine-learning 

Decision tree can be used for classification and regression. 

# Decision Tree Learning Algorithm
![[Pasted image 20221201233601.png]]
* examples: number of rows of data
	* each example has one class label, and list of attributes
* Consider 3 base cases in the learning algorithm:
	1. Examples is empty
		If no examples in the dataset, that means this combination attributes is unseen before. Therefore you have no information to update your belief of the class of the data, thus a neutral *default* class label is returned. 
	2. All examples have the same class label
		Kind of like P(label | attributes = a1 a2 a3 ...) = 1 in the training sample. Then the best choice is to return label.
	3. Attributes is empty
		That is all attributes have been used to differentiate the data, but still can see examples from different classes, that means either there is some hidden noise or the class is fundamentally random given the attributes.
		Here, the choice is to return the majority label of the class.
		A better approach is to return the probability distribution of classes given this attribute combination.
* The recursive case is so:
	* Choose a decision boundary that have the highest information gain
	* Create node for each value of the best attribute
	* Recursively create subtree


# Bootstrapping


# Bagging


# Random Forest (improved bagging)
Usually each bagging tree is quite similar, the variance tends to small.
To increase the variance, we only allow for a random set of attributes to be chosen at each iteration.
