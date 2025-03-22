# Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student

## AIM:
To write a program to implement the the Logistic Regression Model to Predict the Placement Status of Student.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the required packages and print the present data.
2. Print the placement data and salary data.
3. Find the null and duplicate values.
4. Using logistic regression find the predicted values of accuracy , confusion matrices.
## Program:
```

Program to implement the the Logistic Regression Model to Predict the Placement Status of Student.
Developed by:VAISHNAVIDEVI V
RegisterNumber:212223040230

```
```
import pandas as pd
data=pd.read_csv("/content/Placement_Data.csv")
data.head()
```
![Screenshot 2024-10-16 155509](https://github.com/user-attachments/assets/371b9048-d88c-4fe6-be70-126ca948257c)
```
data1=data.copy()
data1=data1.drop(["sl_no","salary"],axis=1)#Removes the specified row or column
data1.head()
```
![Screenshot 2024-10-16 155631](https://github.com/user-attachments/assets/a54ed61e-e1d1-43a4-a3c8-ceb1b92bf29b)
```
data1.isnull().sum()
```
![image](https://github.com/user-attachments/assets/15be1bad-0fe6-469c-909c-c5a46fb19c58)
```
data1.duplicated().sum()
```
![image](https://github.com/user-attachments/assets/69284523-b654-4961-9dca-79d75bbed830)
```
from sklearn.preprocessing import LabelEncoder
le=LabelEncoder()
data1["gender"]=le.fit_transform(data1["gender"])
data1["ssc_b"]=le.fit_transform(data1["ssc_b"])
data1["hsc_b"]=le.fit_transform(data1["hsc_b"])
data1["hsc_s"]=le.fit_transform(data1["hsc_s"])
data1["degree_t"]=le.fit_transform(data1["degree_t"])
data1["workex"]=le.fit_transform(data1["workex"])
data1["specialisation"]=le.fit_transform(data1["specialisation"])
data1["status"]=le.fit_transform(data1["status"])
data1
```
![image](https://github.com/user-attachments/assets/90489b81-6a98-4097-93a6-b7d110f88f2c)
```
x=data1.iloc[:,:-1]
x
```
![image](https://github.com/user-attachments/assets/b096d4d5-c419-495b-893c-98c41a2c9202)
```
y=data1["status"]
y
```
![image](https://github.com/user-attachments/assets/5e2ecad1-03f3-4467-a0a1-2cabd260826f)
```
from sklearn.model_selection import train_test_split
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.2,random_state=0)
from sklearn.linear_model import LogisticRegression
lr=LogisticRegression(solver="liblinear")# A library for large linear classification
lr.fit(x_train,y_train)
y_pred=lr.predict(x_test)
y_pred
```
![image](https://github.com/user-attachments/assets/27729d1d-6504-47a4-87d2-25c6e443f7d4)
```
from sklearn.metrics import accuracy_score
accuracy=accuracy_score(y_test,y_pred)# Accuracy Score = (TP+TN)/
#accuracy_score(y_true,y_prednormalize=False)
accuracy
```
![image](https://github.com/user-attachments/assets/bbc81b26-5787-4303-be30-a150dabd72d0)
```
from sklearn.metrics import confusion_matrix
confusion = (y_test,y_pred)
confusion
```
![Screenshot 2024-10-16 160301](https://github.com/user-attachments/assets/dc2098a7-68ef-4b77-9ce9-e7320a1e6104)
```
from sklearn.metrics import classification_report
classification_report1=classification_report(y_test,y_pred)
print(classification_report1)
```
![image](https://github.com/user-attachments/assets/9abeea08-8830-4742-9244-64ad8e1f9d23)

## Result:
Thus the program to implement the the Logistic Regression Model to Predict the Placement Status of Student is written and verified using python programming.
