# Developing a Neural Network Regression Model

## AIM
To develop a neural network regression model for the given dataset.

## THEORY
Regression problems involve predicting a continuous output variable based on input features. Traditional linear regression models often struggle with complex patterns in data. Neural networks, specifically feedforward neural networks, can capture these complex relationships by using multiple layers of neurons and activation functions. In this experiment, a neural network model is introduced with a single linear layer that learns the parameters weight and bias using gradient descent.

## Neural Network Model
Include the neural network model diagram.

## DESIGN STEPS
### STEP 1: Generate Dataset

Create input values  from 1 to 50 and add random noise to introduce variations in output values .

### STEP 2: Initialize the Neural Network Model

Define a simple linear regression model using torch.nn.Linear() and initialize weights and bias values randomly.

### STEP 3: Define Loss Function and Optimizer

Use Mean Squared Error (MSE) as the loss function and optimize using Stochastic Gradient Descent (SGD) with a learning rate of 0.001.

### STEP 4: Train the Model

Run the training process for 100 epochs, compute loss, update weights and bias using backpropagation.

### STEP 5: Plot the Loss Curve

Track the loss function values across epochs to visualize convergence.

### STEP 6: Visualize the Best-Fit Line

Plot the original dataset along with the learned linear model.

### STEP 7: Make Predictions

Use the trained model to predict  for a new input value .

## PROGRAM

### Name: Arunsamy D

### Register Number: 212224240016

```python
class Model(nn.Module):
    def __init__(self, in_features, out_features):
        super().__init__()
        #Include your code here

        self.linear_layer = nn.Linear(in_features=in_features, out_features=out_features)

    def forward(self, input_tensor):
        #Include your code here
        return self.linear_layer(input_tensor)

# Initialize the Model, Loss Function, and Optimizer

torch.manual_seed(59)  # Ensure same initial weights
model = Model(1, 1)

loss_function = nn.MSELoss()
optimizer = torch.optim.SGD(
    model.parameters(),
    lr=0.001
)

# Train the Model
epochs = 100
losses = []

for epoch in range(1, epochs + 1):  # Loop over epochs
    #Include your code here

    predicted_output = model(input_data)

    loss = loss_function(predicted_output, target_data)

    losses.append(loss.item())

    optimizer.zero_grad()

    loss.backward()

    optimizer.step()

    # Print loss, weight, and bias for EVERY epoch
    print(f'epoch: {epoch:2}  loss: {loss.item():10.8f}  '
          f'weight: {model.linear_layer.weight.item():10.8f}  '
          f'bias: {model.linear_layer.bias.item():10.8f}')
```

### Dataset Information

<img width="523" height="1014" alt="image" src="https://github.com/user-attachments/assets/2e3cedd3-d41d-4a9d-9d75-80a7bb3ab830" />
<img width="449" height="1006" alt="image" src="https://github.com/user-attachments/assets/2cdc7db2-fd6f-4d5d-9a3b-4ba057e75443" />


<img width="571" height="455" alt="download" src="https://github.com/user-attachments/assets/695d3a22-fc56-4232-9b72-bdea40e3c2e9" />


### OUTPUT
Training Loss Vs Iteration Plot

<img width="580" height="455" alt="download" src="https://github.com/user-attachments/assets/e1e59076-855d-42ae-9b19-84a8f7ef765e" />

Best Fit line plot

<img width="571" height="455" alt="download" src="https://github.com/user-attachments/assets/48b43e4a-a59d-417c-be84-4c5f0f73b74f" />

### New Sample Data Prediction
<img width="940" height="296" alt="image" src="https://github.com/user-attachments/assets/7bc3a602-c3b4-4332-afe8-ded774102100" />


## RESULT
Thus, a neural network regression model was successfully developed and trained using PyTorch.
