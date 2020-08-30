# KNN
# hare krishna
# Radhe Radhe

# Table of Contents

When do we use KNN algorithm?
How does the KNN algorithm work?
How do we choose the factor K?
Breaking it Down – Pseudo Code of KNN
Implementation in Python from scratch
Comparing our model with scikit-learn
 

# When do we use KNN algorithm?
KNN can be used for both classification and regression predictive problems. However, it is more widely used in classification problems in the industry. To evaluate any technique we generally look at 3 important aspects:

1. Ease to interpret output

2. Calculation time

3. Predictive Power

Let us take a few examples to  place KNN in the scale :

Model comparisonKNN algorithm fairs across all parameters of considerations. It is commonly used for its easy of interpretation and low calculation time.

 

# How does the KNN algorithm work?
Let’s take a simple case to understand this algorithm. Following is a spread of red circles (RC) and green squares (GS) :

scenario1You intend to find out the class of the blue star (BS). BS can either be RC or GS and nothing else. The “K” is KNN algorithm is the nearest neighbor we wish to take the vote from. Let’s say K = 3. Hence, we will now make a circle with BS as the center just as big as to enclose only three datapoints on the plane. Refer to the following diagram for more details:

scenario2The three closest points to BS is all RC. Hence, with a good confidence level, we can say that the BS should belong to the class RC. Here, the choice became very obvious as all three votes from the closest neighbor went to RC. The choice of the parameter K is very crucial in this algorithm. Next, we will understand what are the factors to be considered to conclude the best K.

 

# How do we choose the factor K?
First let us try to understand what exactly does K influence in the algorithm. If we see the last example, given that all the 6 training observation remain constant, with a given K value we can make boundaries of each class. These boundaries will segregate RC from GS. In the same way, let’s try to see the effect of value “K” on the class boundaries. The following are the different boundaries separating the two classes with different values of K.

K judgement

K judgement2

If you watch carefully, you can see that the boundary becomes smoother with increasing value of K. With K increasing to infinity it finally becomes all blue or all red depending on the total majority.  The training error rate and the validation error rate are two parameters we need to access different K-value. Following is the curve for the training error rate with a varying value of K :

training errorAs you can see, the error rate at K=1 is always zero for the training sample. This is because the closest point to any training data point is itself.Hence the prediction is always accurate with K=1. If validation error curve would have been similar, our choice of K would have been 1. Following is the validation error curve with varying value of K:

training error_1This makes the story more clear. At K=1, we were overfitting the boundaries. Hence, error rate initially decreases and reaches a minima. After the minima point, it then increase with increasing K. To get the optimal value of K, you can segregate the training and validation from the initial dataset. Now plot the validation error curve to get the optimal value of K. This value of K should be used for all predictions.

The above content can be understood more intuitively using our free course – K-Nearest Neighbors (KNN) Algorithm in Python and R

Breaking it Down – Pseudo Code of KNN
We can implement a KNN model by following the below steps:

# Load the data
Initialise the value of k
For getting the predicted class, iterate from 1 to total number of training data points
Calculate the distance between test data and each row of training data. Here we will use Euclidean distance as our distance metric since it’s the most popular method. The other metrics that can be used are Chebyshev, cosine, etc.
Sort the calculated distances in ascending order based on distance values
Get top k rows from the sorted array
Get the most frequent class of these rows
Return the predicted class
Implementation in Python from scratch
We will be using the popular Iris dataset for building our KNN model. You can download it from here.


# Comparing our model with scikit-learn
from sklearn.neighbors import KNeighborsClassifier
neigh = KNeighborsClassifier(n_neighbors=3)
neigh.fit(data.iloc[:,0:4], data['Name'])

# Predicted class
print(neigh.predict(test))

-> ['Iris-virginica']

# 3 nearest neighbors
print(neigh.kneighbors(test)[1])
-> [[141 139 120]]

We can see that both the models predicted the same class (‘Iris-virginica’) and the same nearest neighbors ( [141 139 120] ). Hence we can conclude that our model runs as expected.
