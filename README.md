# Fashion Mnist 

## Exploratory Data Analysis + Data Visualization + Deep Learning Modelling 

### 1 - Abstract

In this project I made Exploratory Data Analysis, Data Visualisation and lastly Modelling. Fashion Mnist Dataset contains 70000 row in two files. Each example is 28x28 image and associated with __10__ labels(targets). After examining the dataset I made data preprocessing for reshaping columns from __784__ to __(28,28,1)__ and save the target feature as a seperate vector. In modelling part, with a sequential model with multiple convolution layers with __50__ Epochs for training the data. For prediction overfitting and underfitting I adjust Dropout Layers. Overally, model gives __0.9236__ accuracy. Furthermore with Data augmentation and/or incresing data size can be helpful for taking better result. 

### 2 - Data
Fashion-MNIST is a dataset of Zalando's article images consisting of a training set of __60,000__ examples and a test set of 10,000 examples. Each example is a __28x28__ grayscale image, associated with a label from __10__ labels.Each image is 28 pixels in height and 28 pixels in width, for a total of 784 pixels in total. Each pixel has a single pixel-value associated with it, indicating the lightness or darkness of that pixel, with higher numbers meaning darker. This pixel-value is an integer between 0 and 255. The training and test data sets have 785 columns. The first column consists of the class labels (see above), and represents the article of clothing. The rest of the columns contain the pixel-values of the associated image.

* To locate a pixel on the image, suppose that we have decomposed x as x = i * 28 + j, where i and j are integers between 0 and 27. The pixel is located on row i and column j of a 28 x 28 matrix.
* For example, pixel31 indicates the pixel that is in the fourth column from the left, and the second row from the top, as in the ascii-diagram below.
* Each row is a separate image.
* Column 1 is the class label.
* Remaining columns are pixel numbers (784 total).
* Each value is the darkness of the pixel (1 to 255).

Each training and test example is assigned to one of the following labels:

* __0 T-shirt/top__
* __1 Trouser__
* __2 Pullover__
* __3 Dress__
* __4 Coat__
* __5 Sandal__
* __6 Shirt__
* __7 Sneaker__
* __8 Bag__
* __9 Ankle boot__

<p align="center">
  <img width="500" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/train%20data%20example.png">
</p>
<p align="center">
     <b>Train Dataset Example</b>
</p>

<p align="center">
  <img width="500" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/test%20data%20example.png">
</p>
<p align="center">
   <b>Test Dataset Example</b>
</p>

### 3 - Exploratory Data Analysis

Firstly, I checked data, which came two different dataset which are train and test. Later I checked distribution of labels in datasets and I create a list for expressing images for both datasets, moreover I see all the classes(labels) equally distributed. So I dont need to do Oversampling or Undersampling. 

### 4 - Data Preprocessing

For preparing datasets to the model I made data processing which is reshaping columns from (784) to (28,28,1), and for seperate vector I save label feature then process test and train data. After that I split train set into train and validation dataset. Validation set contains %30 of original train dataset and split will be 0.7/0.03. Later this process I controlled distribution of labels in train dataset and validation dataset.

<p align="center">
  <img width="750" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/number%20of%20items%20in%20each%20class%20in%20dataset.png">
</p>
<p align="center">
   <b>Number of Items in Each Class in Dataset</b>
</p>

<p align="center">
  <img width="750" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/number%20of%20items%20in%20each%20class%20in%20validation%20dataset.png">
</p>
<p align="center">
   <b>Number of Items in Each Class in Validation Dataset</b>
</p>

### 5 - Modelling 

I used Sequential model. The sequential model is appropriate for a plain stack of layers where each layer has exactly one input tensor and one output tensor. Then I add Conv2D layer, MaxPooling2D, Flatten and Dense. For each layer I used these parameters.

__1.Conv2D__
* filters = 32
* kernel_size = (3,3)
* activation function = relu 
* kernel_initializer = normal
* input_shape = (28,28,1)

__2.MaxPooling2D__
* pool_size = (2,2)


__3.Conv2D__
* filters = 64
* kernel_size = (3,3)
* activation function = relu 

__4.Flatten__


A flatten operation on a tensor reshapes the tensor to have the shape that is equal to the number of elements contained in tensor non including the batch dimension and doesnt need any parameters.

__5.Dense__


In first Dense Layer,
* units = 128
* activation function = relu


In second Dense Layer,
* units = 10
* activation function = softmax

Finally I am compiling model according these parameters,

* loss = categorical cross entrophy
* optimizer = adam
* metrics = accuracy

### 6 - Result & Future Work

As a result, my model gives overally good results. 

<p align="center">
  <img width="750" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/accuracy.png">
</p>
<p align="center">
   <b>Accuracy of the Model</b>
</p>

<p align="center">
  <img width="750" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/loss.png">
</p>
<p align="center">
   <b>Loss of the Model</b>
</p>

Test Loss is __0.2166__


Test Accuracy is __0.9236__


<p align="center">
  <img width="500" height="400" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/classification%20report.png">
</p>
<p align="center">
   <b>Classification Report</b>
</p>
<p align="center">
  <img width="500" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/true%20prediction.png">
</p>
<p align="center">
   <b>Correctly Predicted Items</b>
</p>
<p align="center">
  <img width="500" height="500" src="https://github.com/HalukSumen/FashionMnist/blob/main/images/false%20prediction.png">
</p>
<p align="center">
   <b>Falsely Predicted Items</b>
</p>




The Best accuracy is for Trousers(Class 1), Sandals(Class 5) with __0.99__ and worst accuracy is Shirt(Class 6) with __0.78__.


The Best recall is for Trousers(Class 1), with __0.99__ and worst recall is Shirt(Class 6) with __0.79__


The Best F-1 Score is for Trousers(Class 1) with __0.99__ and worst F-1 Score is Shirt(Class 6) with __0.78__


For better results, data augmentation can be implemented or data size can be expandable. 

