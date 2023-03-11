# Fatigue-Detection
This is a personal project that aims to detect levels of fatigue in a person using facial data. 
The project uses idea from the paper ["FaceNet: A Unified Embedding for Face Recognition and Clustering"](http://arxiv.org/abs/1503.03832).

## Description
Long term fatigue may develop into chronic syndrome and eventually harm a person's physical and mental health. Some system needs to be designed to assess tiredness of a person to avoid short term fatigue to be developed into chronic fatigue. Many system exists to detect short term fatigue in a person but most use only eye aperture as a critera to assess levels of fatigue which might be good for detecting driver drowsiness but, performs poorly in detecing long term fatigue.

Other facial cues like under-eyes, nose, skin and mouth might also help in detecting fatigue. We can use algorithms like Facenet to extract a vector of embeddings for these features. A classification model then can be trained using this data.

## Proposal
In this project I aim to develop a efficient way to detect fatigue in person. The goal is to detect fatigue in person using a single image. 
Facial points like eyes, under-eyes, nose, skin and mouth are important for detecting fatigue. We use embedding extracted using Facenet or some other algorithm to train a classification model.

## Training Data
A custom dataset is used for training the model. Train data consist of 317 images for both the classes over 9 identities. After filtering the dataset some performance improvements were seen.

## Pre-processing

### Face aligment using MTCNN
Some other detectors like Dlib seems to be less costly in detecting faces but misses some of the hard examples. Also it was observed that number of false positives were also high.

Although more costly [MTCNN](https://kpzhang93.github.io/MTCNN_face_detection_alignment/index.html) seemed to work very well in the settings provided.

### Extract Embeddings using Facenet
I used the keras implementation of [Facenet](https://pypi.org/project/keras-facenet/) to extract a vector of embeddings from the cropped images. You can follow up this implementation on this [repo](https://github.com/davidsandberg/facenet).


### Training
Extracted features can be normalized before training. But in this case it doesn't seemed to matter much.
A kernel-SVM is trained using processed data.


### Performance 
The accuracy on testing set is 86%. 
The classification report is:


||precision|    recall|  f1-score|   support|
|-----|---------|----------|----------|----------|
|0|     0.91|      0.88|      0.90|        34|
|1|    0.78 |     0.82 |     0.80 |       17 |


