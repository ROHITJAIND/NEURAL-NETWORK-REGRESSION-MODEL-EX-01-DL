# EX-01 Developing a Neural Network Regression Model
### Aim:
To develop a neural network regression model for the given dataset.&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**DATE: 19.08.2024**

### Theory:
Design and implement a neural network regression model to accurately predict a continuous target variable based on a set of input features within the provided dataset. The objective is to develop a robust and reliable predictive model that can capture complex relationships in the data, ultimately yielding accurate and precise predictions of the target variable. The model should be trained, validated, and tested to ensure its generalization capabilities on unseen data, with an emphasis on optimizing performance metrics such as mean squared error or mean absolute error.

### Neural Network Model:
![image](https://github.com/user-attachments/assets/151f56b9-8129-4253-a9c3-744ab9c77732)

### Design Steps:

- STEP 1:Loading the dataset
- STEP 2:Split the dataset into training and testing
- STEP 3:Create MinMaxScalar objects ,fit the model and transform the data.
- STEP 4:Build the Neural Network Model and compile the model.
- STEP 5:Train the model with the training data.
- STEP 6:Plot the performance plot
- STEP 7:Evaluate the model with the testing data.

## Program:
```python
import pandas as pd
from sklearn.preprocessing import MinMaxScaler
from sklearn.model_selection import train_test_split as tts
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
df=pd.read_csv("data.csv")
df.head()
df.describe()
df.info()
X=df[["Input"]].values
Y=df[["Output"]].values
xtrain,xtest,ytrain,ytest=tts(X,Y,test_size=0.3,random_state=0)
scaler=MinMaxScaler()
scaler.fit(xtrain)
xtrainscaled=scaler.transform(xtrain)
model=Sequential([Dense(units=4,activation='relu',input_shape=[1]),
                  Dense(units=6,activation='relu'),
                  Dense(units=4,activation='relu'),
                  Dense(units=1)])
model.compile(optimizer='rmsprop',loss='mse')
model.fit(xtrainscaled,ytrain,epochs=2000)
loss=pd.DataFrame(model.history.history)
loss.plot()
xtestscaled=scaler.transform(xtest)
model.evaluate(xtestscaled,ytest)
p=[[5]]
pscale= scaler.transform(p)
model.predict(pscale)

```
### Output:

##### Dataset Information:
**df.head()**&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**df.info()**&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**df.describe()**<br>
<img align=top src="https://github.com/user-attachments/assets/c9c19465-2db0-47f8-afb6-49633f892aa6">&emsp;&emsp;&emsp;
<img align=top  src="https://github.com/user-attachments/assets/c08ce734-2b92-42fb-adf5-0ea3b55e993b">&emsp;&emsp;&emsp;
<img align=top  src="https://github.com/user-attachments/assets/bde44ad2-8c90-462e-b899-1cd29ec15625">

##### Training Loss Vs Iteration Plot:
<img src="https://github.com/user-attachments/assets/67e285f9-96a0-4bee-b8ef-1c40e77f274f">

##### Test Data Root Mean Squared Error:
<img src="https://github.com/user-attachments/assets/1a3fd13b-241b-4920-946d-baf3e7680d8b">

##### New Sample Data Prediction:
<img src="https://github.com/user-attachments/assets/5ea5ea88-e70c-425d-933b-dc7b08cd5560">

### Result:
Thus a neural network regression model for the given dataset is developed and the prediction for the given input is obtained accurately.
<br>
<br>
**Developed By: ROHIT JAIN D - 212222230120**
