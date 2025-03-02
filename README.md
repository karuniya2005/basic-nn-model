# Developing a Neural Network Regression Model

## AIM

To develop a neural network regression model for the given dataset.

## THEORY

First import the libraries that we will use Import the dataset and check the types of the columns Now build your training and test set from the dataset Here we are making the neural network 2 hidden layers with 1 output and input layer and an activation layer as relu and with their nodes in them. Now we will fit our dataset and then predict the value.

## Neural Network Model
![Screenshot 2024-03-17 204822](https://github.com/karuniya2005/basic-nn-model/assets/161425769/f4a8f76a-83d5-41d5-afc6-862efc8e1c70)

## DESIGN STEPS

### STEP 1:

Loading the dataset

### STEP 2:

Split the dataset into training and testing

### STEP 3:

Create MinMaxScalar objects ,fit the model and transform the data.

### STEP 4:

Build the Neural Network Model and compile the model.

### STEP 5:

Train the model with the training data.

### STEP 6:

Plot the performance plot

### STEP 7:

Evaluate the model with the testing data.

## PROGRAM
### Name: KARUNIYA M
### Register Number: 212223240068
```
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import MinMaxScaler
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from google.colab import auth
import gspread
from google.auth import default
auth.authenticate_user()
creds, _ = default()
gc = gspread.authorize(creds)
worksheet = gc.open('clinical').sheet1
data = worksheet.get_all_values()
dataset1 = pd.DataFrame(data[1:], columns=data[0])
dataset1 = dataset1.astype({'actual':'float'})
dataset1 = dataset1.astype({'predicted':'float'})
dataset1.head()
X = dataset1[['actual']].values
y = dataset1[['predicted']].values
X
X_train,X_test,y_train,y_test = train_test_split(X,y,test_size = 0.33,random_state = 33)
Scaler = MinMaxScaler()
Scaler.fit(X_train)
X_train1 = Scaler.transform(X_train)
ai_brain = Sequential([
    Dense(6,activation = 'relu'),
    Dense(6,activation = 'relu'),
    Dense(1)
])
ai_brain.compile(optimizer = 'rmsprop', loss = 'mse')
ai_brain.fit(X_train1,y_train,epochs = 4000)
loss_df = pd.DataFrame(ai_brain.history.history)
loss_df.plot()
X_test1 = Scaler.transform(X_test)
ai_brain.evaluate(X_test1,y_test)
X_n1 = [[30]]
X_n1_1 = Scaler.transform(X_n1)
ai_brain.predict(X_n1_1)

```
## Dataset Information
![Screenshot 2024-03-17 204444](https://github.com/karuniya2005/basic-nn-model/assets/161425769/19cb2dbc-1537-4515-8018-131c7542cc46)

![Screenshot 2024-03-17 204436](https://github.com/karuniya2005/basic-nn-model/assets/161425769/14ea89dc-c888-45b9-869a-f01c709a4dfc)

## OUTPUT

### Training Loss Vs Iteration Plot
![Screenshot 2024-03-17 204500](https://github.com/karuniya2005/basic-nn-model/assets/161425769/76dcb462-6466-41dd-9328-02abc7350893)


### Test Data Root Mean Squared Error
![Screenshot 2024-03-17 204507](https://github.com/karuniya2005/basic-nn-model/assets/161425769/97bf453f-b25f-468b-a273-22e0fe940958)


### New Sample Data Prediction

![Screenshot 2024-03-17 204518](https://github.com/karuniya2005/basic-nn-model/assets/161425769/b9b7645a-db30-4f26-987f-d489fce34377)


## RESULT

A neural network regression model for the given dataset has been developed Sucessfully.
