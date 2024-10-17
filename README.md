# EX 5 Implementation of Logistic Regression Using Gradient Descent
## DATE:
## AIM:
To write a program to implement the the Logistic Regression Using Gradient Descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Initialization: Sets the learning rate and the number of iterations.
2. Sigmoid Function: Defines the logistic function for outputting probabilities.
3. Fit Method: Adjusts weights using gradient descent based on the difference between predicted and actual values.
4. Predict Method: Returns class predictions based on the learned weights.

## Program:
```
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: Madhu Mitha V
RegisterNumber:  2305002013
import pandas as pd
import numpy as np
data=pd.read_csv("/content/ex45Placement_Data.csv")
data.head()
data1=data.copy()
data1.head()
data1=data1.drop(['sl_no','salary'],axis=1)
data1
X=data1.iloc[:,:-1]
Y=data1["status"]
theta=np.random.randn(X.shape[1])
y=Y
def sigmoid(z):
  return 1/(1+np.exp(-z))
def loss(theta,X,y):
  h=sigmoid(X.dot(theta))
  return -np.sum(y*np.log(h)+ (1-y) * np.log(1-h))
def gradient_descent(theta,X,y,alpha,num_iterations):
  m=len(y)
  for i in range(num_iterations):
    h=sigmoid(X.dot(theta))
    gradient=X.T.dot(h-y)/m
    theta-=alpha*gradient
  return theta
theta=gradient_descent(theta,X,y,alpha=0.01,num_iterations=1000)
def predict(theta,X):
  h=sigmoid(X.dot(theta))
  y_pred=np.where(h>0.5 , 1 ,0)
  return y_pred
y_pred=predict(theta,X)
accuracy=np.mean(y_pred.flatten()==y)
print("Accuracy:",accuracy)
print("Predicted:\n",y_pred)
print("Actual:\n",y.values)
xnew=np.array([[0,87,0,95,0,2,78,2,0,0,1,0]])
y_prednew=predict(theta,xnew)
print("Predicted Result:",y_prednew)
```

## Output:
![image](https://github.com/user-attachments/assets/154419c1-e5ad-4f9c-84e6-834a5aa1a22f)
![image](https://github.com/user-attachments/assets/4a0ab3ee-405c-4019-a027-fe48ad083199)


## Result:
Thus the program to implement the the Logistic Regression Using Gradient Descent is written and verified using python programming.

