# Calculator
Recognizes Handwritten digits and operators, gives solution to operation

For task 1:

A simple CNN model was trained using keras
and 1000 images from the dataset provided.
The exact same model is used in task 2 for 
predicting the order of digits and arithmetic symbols.

For task 2:

The task was split into three parts among the team members:
1. Predicting Label: The model used for task 1 was used for 
predicting the order of digits and arithmetic symbols.
The Image was then split into three equal parts and according
to the order predicited, images were passed to appropriate models.

For the next two parts, an external dataset was used to train the models.
The dataset consisted of math symbols and digits. We deleted the unrequired
folders and renamed the folders with appropriate names. The finally used dataset
has been included in the 'Model training files' folder.
The link to the original dataset is : "https://www.kaggle.com/clarencezhao/handwritten-math-symbol-dataset"

2. Predicting Arithmetic Symbol: The image containing the arithmetic
symbol was passed to the arithmetic symbol model.In this, A Support Vector Machine (SVM)
model was used with a regularisation parameter of 10 gamma (kernel coefficient) as 0.005
and Radial Basis Function (rbf) Kernel. All implemented using python library named
scikit learn and some helping library stated in requierments.

3. Predicting Digits: The images containing the numerical digits were passed
to the digit classification model. A simple CNN model was used for predicting the digits.
The process of training the model was as described:
	1) Took a a set of training images for each digits from 0-9, each with a set of around 550 images. 
	2) Then we extracted the images to create a training data and converted it into numpy array to convert it into readable format.
	3) To train the model and test its accuracy,  we split the dataset into X_train , X_test with test size =0.1 , similarly the training labels
	 i.e the target will also be split into y_train and y_test
	4) Then encoded the target labels (y)
	5) To train the dataset, created  a Sequential model with 5 Convolutional layers using ReLU and input shape of our inages (32, 32,3)
	6) Also we used MaxPooling for Pooling qnd Batch Normalization to enchance the performance of the model
	7) After compiling our model with Adam Optimizer, fitting thw model, we received a validation accuracy of 95.35%
	8) Thus, after testing on multiple images, it was detecting almost all the images accurately.

Finally a function named 'result' compiles all three steps and then preforms the 
appropriate calculation according to operands and operator predicited.

-------------------------------------------------------------------------------------
Some other methods that we tried:
1.Clustering: We tried splitting each image in the dataset
into three equal parts and then using KNN clustering (n_clusters=14)
along with PCA with different values for n_dimensions on those images.
The results were not satisfactory and we decided to ditch that idea.

2.RNN: We tried implementing Recurrent Neural Network by padding the 
keras (28,28) MNIST dataset to (32,32) as when resize the 3 parted competetion images of (128,128) to (28,28)
much features are lost in image so we resized them to (32,32). On this processed MNIST accuracy was great
but it was not performing well on competetion images.

3.K-Means and Decision Tree: both this were not able to perform as good as the final model created.

5. Random Forest: We tried to train the model using images of operators
 with Random Forest. However, it gave an accuracy of 83% on validation data, 
 hence we opted for SVM instead which had given a higher accuracy.

6. Data Augmentation: In an attempt to increase the accuracy, we increased number 
of images through data augmentation, i.e using Data Generator from Keras. However, 
due to uneven changes, this step reduced the accuracy drastically from 95% to 9%.
Hence, we discarded it.


The model gave the following results:
![Screenshot 2022-04-12 134601](https://user-images.githubusercontent.com/77509449/162914126-51d5d6e1-e9f1-4e1b-adb9-9e0b34c58f34.png)
![Screenshot 2022-04-12 134653](https://user-images.githubusercontent.com/77509449/162914240-f75da1dc-df4e-454a-af8e-029998b53af2.png)

