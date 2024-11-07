# **Transaction Fraud Prediction**

In this small project we will create a model that is capable of identifying fraudulent transactions in the cryptocurrency sector.<br>
Cryptocurrencies are forms of digital currency that use cryptography to ensure secure transactions and to control the creation of new units.<br>
They operate on a technology called blockchain, which is a type of distributed and decentralized digital ledger.<br>


<img src="image\criptcoin.jpeg" alt="criptocoin">

This is a relatively simple project with an emphasis on data preprocessing with pipelines created from classes. <br>
This makes data manipulation simpler and easier to understand, as well as making the code more structured and clean.


### Creation of the Pre-Processing Pipeline

**BaseEstimator**: This is the base class for all estimators in scikit-learn. An estimator is any object that can estimate some parameters based on a set of data. For example, a Machine Learning algorithm like a linear regression or a decision tree is an estimator. The BaseEstimator class provides basic functionality, such as methods for setting the parameters of an estimator and for obtaining these parameters with get_params() and set_params().

**TransformerMixin**: This is a mixed class (mixin) used to add transformation functionality to an estimator. In scikit-learn, a "transformer" is a type of estimator that can transform a set of data. For example, it can be used to normalize or standardize data, select or extract features, etc. The TransformerMixin class adds the fit_transform() method, which is a convenient method that first fits the transformer to the data set (using fit()) and then applies the transformation to the same data set (using transform()). This is useful to avoid having to call fit() and transform() separately during data preprocessing.

The combination of these two classes is often used when creating a custom estimator or transformer with scikit-learn. By inheriting from these classes, you ensure that your custom estimator integrates well with other scikit-learn functionality, such as pipelines and other modeling tools.


### Pipe-class
class PipeSteps
- Constructor method to initialize the class with a list of columns.
- Assigning the columns argument to the self.columns instance attribute.
- Método fit usado para ajustar (treinar) a transformação nos dados de treinamento.
- Returns the instance itself, indicating that the method makes no modifications.
- Transform method to transform input data.
- Makes a copy of the input data to avoid altering the original data.
- Returns data without modifications.

class SelectColumns
- Defining a class that inherits from PipeSteps.
- Transform method to transform input data.
- Makes a copy of the input data to avoid altering the original data.
- Selects and returns only the columns specified in self.columns.

class class FillData
- Defining a class that inherits from PipeSteps.
- Fit method to fit the transformation on training data.
- Calculates the mean of each column specified in self.columns and stores it in the self.means dictionary.
- Returns the instance itself, indicating that the method makes no modifications.
- Transform method to transform input data.
- Makes a copy of the input data to avoid altering the original data.
- Iterates over each column specified in self.columns.
- Fills missing values ​​in the column with the average calculated in the adjustment phase.
- Returns the transformed data.

class StandardizeData
- Defining a class that inherits from PipeSteps.
- Fit method to adjust the scaler on training data.
- Initializes a StandardScaler instance to standardize data.
- adjusts the scaler on the columns specified in self.columns.
- Returns the instance itself, indicating that the method makes no modifications.
- Transform method to transform input data.
- Makes a copy of the input data to avoid altering the original data.
- Applies the standardization transformation to the specified columns.
- Returns the transformed data.

class GetData
- Defining a class that inherits from PipeSteps.
- Transform method to transform input data.
- Makes a copy of the input data to avoid altering the original data.
- Returns DataFrame values ​​as a NumPy array.

Pipeline in scikit-learn is a tool that chains several transformation steps and a final estimator into a single object. This allows you to set up a machine learning process that includes preprocessing steps (such as normalization, standardization, and feature extraction) followed by the application of a machine learning model. Each pipeline step is represented by a tuple containing a name and a transformation object or model.

### Model
- **input layer**: Create the input layer based on the size of the "attributes".
- **hidden layers**: Added three hidden layers with len(attribute), 20 and 5 units (neurons) respectively with each using Relu activation.
- **Output layer**: An output with two units, thus generating two percentage predictions and for activation we apply Softmax.

- **Summary**    
<img src="image\summary.png" alt="criptocoin">


### Assessment methods
**Accuracy**: Accuracy is a metric for evaluating classification models. It represents the proportion of correct predictions made by the model in relation to the total samples evaluated. In other words, it is the number of correct predictions divided by the total number of predictions made, indicating how well the model is classifying the samples correctly.In our model we were able to achieve an accuracy of almost 95%.

**AUC**: Area Under the Curve is a metric used to evaluate the performance of binary classification models. It is based on the ROC (Receiver Operating Characteristic) curve, which is a graph that shows the relationship between the true positive rate (sensitivity) and the false positive rate (1 - specificity) for different decision thresholds. The AUC represents the total area under the ROC curve and can range from 0 to 1. An AUC of 0.5 indicates random performance, while an AUC of 1.0 indicates perfect classification. Therefore, the closer the AUC value is to 1, the better the model's ability to distinguish between positive and negative classes. We managed to reach 0.97, demonstrating excellent performance.