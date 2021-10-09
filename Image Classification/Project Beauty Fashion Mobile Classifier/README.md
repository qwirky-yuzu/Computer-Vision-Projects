# Building a simple image classification using Tensorflow

## The Problem
There are hundreds of thousands new products added to Shopee every day. To make relevant products easily discoverable, one fundamental challenge is to accurately extract relevant information from a large volume of products. For the National Data Science Challenge (NDSC) 2019 , the challenge presented this real-world challenge of building an automatic solution to extract product related information through machine learning techniques.

There are 3 broad categories of products for classification:
1. Beauty
2. Fashion
3. Mobile

One of the biggest challenges in product identification and classification is largely due to sellers posting unclear images such as screenshots of their posts, taking pictures at different angles and taking pictures mixed with other product categories. While we can depend on sellers to write up their post on the products that they are selling, a classification algorithm that separates product types into its broad categories will allow us to segment product types more accurately so that customers can search for their items in a more efficient manner.

## The Solution

### 1. Dataset
For the given dataset, the folder sizes for three product categories, are as follow: the beauty images (22GB tar file), fashion images (35.2GB tar file), and mobile images (10.4GB tar file) accordingly. This translates to over 67GB of data and would be computationally impossible based on Colab's Free Tier GPU Ram to load in all the data for training.

As such, the data was sampled randomly with approximately 1100 to 1200 images per class for training and validation and another 3 separate images ranging from easy to hard in classification difficulty was used per class for testing.

### 2. Model
Given that the dataset is a relatively simple one, I opted for a simple model - ResNet50 which was computationally feasible and efficient in training and produces excellent results (see below).  The model was able to differentiate between the 3 categories with relative ease and classify images taken at awkward angles.

To feed the data into the model efficiently, an image will be read from a file, decoded into a tensor, and resized - all using Tensorflow library. This was method is exceptionally elegant and easy to understand - would highly recommend giving it a try!

### 3. Architecture & Augmentation

1. ResNet 50 (Transfer Learning). Froze the base model and trained only the classification layer.
2. Early Stopping
3. Image Augmentation - rotate, flip, image shift (left & right)

### 4. Results

- Training Accuracy: 98.3%
- Validation Accuracy: 97.1%
