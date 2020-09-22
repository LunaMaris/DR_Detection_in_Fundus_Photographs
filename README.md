# Internship_ENTStudios
 Automatic detection of DR in fundus photographs


This repository contains the code I wrote during my internship at ENT Studios. The aim was to create a system that can automatically detect more than mild diabetic retinopahty (DR) in fundus photographs. Two different strategies, based on deep learning were implemented for this.

In the first strategy UNet is used to detect and segment the lesions in the fundus photographs, after which the DR-grade is defined by counting the lesions (per quadrant), following the clinical strategy for DR-grading. In the second strategy VGG16 and ResNet18 are used to directly define the DR-grade from the fundus photographs.

The 'Preprocessing' folder contains all code used to preprocess the images, annotations and labels of the used databases: STARE, DRIVE, CHASEDB1, IDRiD and Kaggle. 
The subfolder 'Preprocessing_Lesion_Segmentation' contains the programs for the preprocessing of the images and corresponding annotations of the STARE, DRIVE, CHASEDB1 and IDRiD databases, which are used in the first strategy. There are separate programs for the preprocessing, augmentation and normalization of the data. And finally also a program to assembel the final arrays, used for training and testing of the UNet.
The subfolder 'Preprocessing_DR_Grading' contains the programs to preprocess the Kaggle images and the corresponding labels, which are used in the second strategy. There are again separate programs for preprocessing and normalizing the data and there is a program to undersample the data and to perform a train-test split to end up with the final arrays that can be used for training and testing of VGG16 and ResNet18.

The folder 'DR_classification' contains all code to train and test the systems used to perform the DR-grading.
The subfolder 'FeatureBasedClassification' contains the code for the first strategy. In the folder 'LesionSegmentation' the code can be found to perform a grid search and to define the right amount of epochs and to train and test two versions of UNet for lesion segmentation. In the folder DR-grading the code can be found to count the lesions from the predicted annotations (per quadrant) and to define the DR-grade based on this.
The subfolder 'DeepLearningClassification' contains the code for the second strategy. Here the code can be found to perform a grid search and to define the right amount of epochs and to train and test both VGG16 and ResNet18 to define the DR-grade from fundus photographs.

All networks were trained using a system of 3 GPUs at ENT Studios.
