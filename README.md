# Fatigue-Detection
This is a personal project that aims to devepol a image classification model using machine learning. 
The project uses idea from the paper ["FaceNet: A Unified Embedding for Face Recognition and Clustering"](http://arxiv.org/abs/1503.03832).

## Description
In this project, I created a dataset consisting of two categories "tired" and "not_tired". Data collection was done under different lighting conditions both indoors and outdoors.
We can use algorithms like Facenet to extract a vector of embeddings for these features. A classification model then can be trained using this data.

## Proposal
In this project I aim to develop a efficient way to image classification using machine learning. We use embedding extracted using Facenet or some other algorithm to train a classification model.

## Training Data
A custom dataset is used for training the model. Data consist of 317 images for both the classes which was collected from few volunteers, few images from a couple of online resources are also used in this data. After filtering the dataset some performance improvements were seen.

If you wish to use the data used in this project then please read agreement in the google form below and give your approval.

[Consent form](https://docs.google.com/forms/d/e/1FAIpQLScEH6ky85dOLDHd9Zr-pR7Ufkwzioahjdek_i1Bsct4DRezJw/viewform?vc=0&c=0&w=1&flr=0&fbzx=-7886685058164827048)

## Pre-processing

### Face aligment using MTCNN
Some other detectors like Dlib seems to be less costly in detecting faces but misses some of the hard examples. Also it was observed that number of false positives were also high.

Although more costly [MTCNN](https://kpzhang93.github.io/MTCNN_face_detection_alignment/index.html) seemed to work very well in different settings.

### Extract Embeddings using Facenet
I used the keras implementation of [Facenet](https://pypi.org/project/keras-facenet/) to extract a vector of embeddings from the cropped images. You can follow up this implementation on this [repo](https://github.com/davidsandberg/facenet).


## Training
Extracted features can be normalized before training. But in this case it doesn't seemed to matter much.
A kernel-SVM is trained using processed data.


## Performance 
The accuracy on testing set is 86%. 
The classification report is:


||precision|    recall|  f1-score|   support|
|-----|---------|----------|----------|----------|
|0|     0.91|      0.88|      0.90|        34|
|1|    0.78 |     0.82 |     0.80 |       17 |

## Conclusion
The model performs well concerning the testing dataset for which the identities were same as the train set. I further did some more testing with some new identities that were not part of the training set, in this case the model seemed to perform poorly espicially for "not_tired" category.
Training model for embeddings extracted from entire face of a person leads to overfitting due to which it performs so poorly for new identities.






