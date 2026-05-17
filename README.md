# Approach

The objective of this project was to build and evaluate a **feed-forward neural network** for predicting customer churn using structured customer data. 
The project focused not only on model performance, but also on understanding how neural networks learn through forward propagation, loss calculation, 
backpropagation, and parameter updates.

The overall approach included-
1 Data preprocessing
2 Neural network model building
3 Training and evaluation
4 Hyperparameter experimentation
5 Performance interpretation


# Steps Followed

## 1️ Data Exploration

The dataset was loaded and analyzed to understand -

1 Number of rows and columns
2 Data types
3 Missing values
4 Statistical summary
5 Distribution of the target variable (Churn)

Key observation -

1 Dataset contained both numerical and categorical features.
2 The target variable was binary:

   0 means Non-churn
   1 means Churn

## 2️ Data Preprocessing

The following preprocessing steps were applied:

### Missing Value Handling

1 Numerical columns → filled using median not required in our case though
2 Categorical columns → filled using mode not required in our case though

### Feature Scaling

Numerical features were standardized using **StandardScaler** to improve neural network learning stability.

### Train-Test Split

The dataset was divided into -  80% training data and 20% testing data

## 3️ Neural Network Model Building

A feed-forward neural network was created using TensorFlow/Keras.

### Model Architecture

1 Input Layer
2 Hidden Layer 1 → ReLU activation
3 Hidden Layer 2 → ReLU activation
4 Output Layer → Sigmoid activation

### Model Configuration

1 Loss Function → Binary Crossentropy
2 Optimizer → Adam
3 Evaluation Metric → Accuracy

## 4️ Model Training

The model was trained using:

1 Batch size = 32
2 Multiple epochs
3 Validation split for monitoring performance

During training:

1 Forward propagation generated predictions
2 Loss was calculated
3 Backpropagation updated weights and biases

## 5️ Model Evaluation

The model was evaluated using:
1 Accuracy
2 Loss
3 Confusion Matrix
4 Precision
5 Recall
6 F1-score

Loss curves and confusion matrix heatmaps were generated for visualization.

# Results

##    Training Performance

* Final Accuracy ≈ 99.45%
* Validation Accuracy ≈ 98.75%
* Validation loss ≈ 4.9%

##  Confusion Matrix Result

[[393   1]
 [  6   0]]

Meaning:

* 393 non-churn customers predicted correctly
* 6 churn customers predicted incorrectly
* No churn customers detected successfully

#  Key Observations

##  1. Severe Class Imbalance

The dataset contained very few churn examples compared to non-churn customers.

This caused the model to:

Predict mostly the majority class (0)


## 2. Accuracy Was Misleading

Although accuracy was ~98%:

* Recall for churn = 0
* F1-score for churn = 0

The model completely failed to identify churn customers.

## 3. Model Bias Toward Majority Class

The neural network learned:
Predicting all customers as non-churn minimizes overall loss.
This is a common issue in imbalanced classification problems.

## 4. Experimentation Findings

Multiple experiments were performed by changing:

1 Hidden layers
2 Neurons
3 Epochs
4 Learning rate
5 Activation functions

Observation -
1 Increasing model complexity alone did not improve churn prediction.
2 Handling imbalance using class weighting improved churn detection more effectively.

# Final Conclusion

The neural network successfully learned patterns from the dataset and achieved high overall accuracy with low loss values. However, due to severe class imbalance,
the model became biased toward predicting non-churn customers and failed to identify churn cases effectively.

This project demonstrated that:

1 Accuracy alone is not sufficient for evaluating classification models.
2 Metrics like recall, F1-score, and confusion matrix are critical in imbalanced datasets.
3 Proper imbalance handling techniques are necessary for reliable churn prediction.

Overall, the project provided practical understanding of:

1 Neural network training
2 Forward propagation
3 Backpropagation
4 Hyperparameter tuning
5 Model evaluation and interpretation.
