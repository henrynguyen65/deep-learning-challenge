Overview:
Alphabet Soup, a nonprofit foundation, seeks a tool to aid in selecting funding applicants with the highest likelihood of success. The objective is to develop a Binary Classifier utilizing dataset features to predict the success of applications for funding by Alphabet Soup.

Results:
Data Preprocessing:
The target feature for the model is 'IS_SUCCESSFUL'.

Features used in model creation:

APPLICATION_TYPE: Alphabet Soup application type
AFFILIATION: Affiliated sector of industry
CLASSIFICATION: Government organization classification
USE_CASE: Use case for funding
ORGANIZATION: Organization type
STATUS: Active status
INCOME_AMT: Income classification
SPECIAL_CONSIDERATIONS: Special considerations for application
ASK_AMT: Funding amount requested
IS_SUCCESSFUL: Was the money used effectively
The 'EIN' and 'NAME' columns were dropped from the original dataset.

Unique values were determined for each column. For columns with over 10 unique values, data points for each unique value were counted. A cutoff point was established based on the number of data points for each unique value to bin "rare" categorical variables together into a new value, "Other". The following features were binned using this method:

APPLICATION_TYPE
CLASSIFICATION
INCOME_AMT
AFFILIATION
USE_CASE
ORGANIZATION
Categorical values were encoded using pandas' 'get_dummies' function.

The dataset was split into training and test sets using the 'train_test_split' function.

Features in the training and testing sets were scaled using Scikit Learn's 'StandardScaler()'.

Compiling, Training, and Evaluating the Model:
A neural network model was constructed using TensorFlow and Keras by specifying the number of input features and nodes for each layer.

The first hidden layer had 60 nodes with 32 input features and utilized 'relu' as the activation function.

The second hidden layer had 24 nodes with 32 input features and also used 'relu' as the activation function.

The output layer employed 'sigmoid' as the activation function.

The model structure was validated, comprising a total of 3469 parameters.

The model was compiled with the loss function set to 'binary_crossentropy', optimizer set to 'adam', and metrics set to 'accuracy'.

Training was conducted using the training dataset for 100 epochs, with weights saved every 5 epochs using a callback function.

After 36 epochs, the trained model achieved an accuracy of 0.5324 and a loss of 0.6911.

For the test data, the model yielded an accuracy of 0.6780 and a loss of 0.8298.

The model was saved to a file in HDF5 format.

However, the model fell short of the target performance of achieving higher than 75% accuracy.

To improve performance, rare categorical values for the following features were binned separately:

INCOME_AMT
AFFILIATION
USE_CASE
ORGANIZATION
For the optimized model, the first hidden layer was adjusted to contain 60 nodes, and the second hidden layer contained 24 nodes.

Other attempted improvements, such as dropping the INCOME_AMT, USE_CASE, and ORGANIZATION columns, and adding three extra hidden layers with 'tanh' as the activation function, did not positively impact the model performance and were consequently removed from consideration.

Summary:
The binary classifier model, developed to predict the selection of funding applications, achieved an accuracy of 67%. Hyperparameter tuning is recommended to develop a model that can deliver better performance.
