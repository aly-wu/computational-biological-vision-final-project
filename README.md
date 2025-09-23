# Exploring biases in facial emotion recognition models for minorities

Final Project for NEUR189B Artificial and Biological Vision, taught by Yuqing Zhu. On testing emerging racial bias in facial emotion recognition models with demographically diverse and non-diverse datasets. 

Authors: Alyssa Wu (Pomona '28) and Brenda Aguilar (Pitzer '26)

To view the introduction, methodology, and results in depth (as well as all the other cool projects from the class!) visit: https://neur189b.sites.pomona.edu/projects/ 

## Introduction 
How well can neural networks recognize emotions in human faces? What key facial features are used by these models to identify and categorize emotion? What are the societal implications of these processes and results? Are these models racist? Let’s find out!

## Methods 
We apply Akhand et. al’s transfer learning methodology on DenseNet-161 to create two models: one which is fine-tuned with images of faces from KDEF (a racially & age-wise non-diverse dataset, set number of models posing, in color) and another is is fine-tuned with images of faces from a much more diverse dataset FER-2013 (random images of faces compiled from Google, B&W). We compare the accuracies of each of the two neural networks when tested with images from facial emotion datasets DiverseFaces (Black and Latino faces across age and sex, set number of models posing, in color) and JAFFE (Japanese women in their 20s, set number of models posing, B&W). All datasets include 7 emotions: happy, anger, disgust, sad, fear, neutral, and suprise EXCEPT DiverseFACES (no suprise). 

## Results
The model built from fine-tuning Dense-Net 161 with images of faces from KDEF is referred to as the KDEF Model, and the model fine-tuned with images of faces from FER-2013 the FER-2013 Model.

### Train/Test Accuracy
The best testing accuracy for the KDEF Model was 96.67 percent. At that same epoch, its training accuracy was 99.40 percent. Such high testing accuracy follows Akhand et al’s findings in their 2021 findings. The best testing accuracy for the FER-2013 Model was 58.45 percent, though for that same epoch, the training accuracy was at 99.45 percent. 

This discrepancy between train and test accuracy in the FER-2013 Model can be explained by the variability of the images in the FER-2013 dataset. Unlike the KDEF and JAFFE datasets (the two dataset in which Akhand et al. test their transfer-learning methods on), the faces in FER-2013 are not standardized in lighting, cropping, or context. Both KDEF and JAFFE are rather homogenous datasets, where models of a singular race are asked to pose according to seven emotions against a standardized background and standardized head orientations and wearing no face-obscuring accessories (like glasses). The FER-2013 dataset is instead composed of miscellaneous images across Google Image Search, introducing a sense of randomness.

### On JAFFE
Out of the 213 images in JAFFE, the KDEF Model accurately labeled 58 out of the 213 images, a 27.23 percent accuracy rate. This is a stark drop from the testing accuracy the KDEF Model has when evaluated with test images from KDEF (96.00 percent). Ironically, the FER-2013 Model, which has a much lower testing accuracy when evaluated on test images from FER-2013 (at 53.59 percent), was able to accurately label more facial emotions in JAFFE. The FER-2013 Model accurately labeled 73 of 213 images, a 34.27 percent accuracy rate. 

### On DiverseFACES
For the DiverseFACES dataset, which model performs better is reversed. The FER-2013 Model was able to correctly label 130 out of the 432 (30.09 percent). The KDEF Model was able to correctly categorize 152 images (35.19 percent accuracy).

Here, it is important to remind ourselves that both the KDEF dataset and DiverseFACES are in color while FER and JAFFE are black and white. 

### Notable Results from the Confusion Matrices
#### KDEF x DiverseFACES
Subsantial accuracy within the KDEF model to classify happiness, neutrality, sadness, and anger. There are significant mislabelings of fear as disgust and disgust as anger. Notably, there is a tendency for the KDEF Model to misclassify all emotions as anger (most frequent classification), a result which does feed into preexisting notions of Black and Latino aggressiveness.

#### KDEF x JAFFE
The KDEF model has a tendency to classify emotions in the JAFFE dataset as surprise. However, there is some level of accuracy in classifying happiness, disgust, and anger. 

#### FER-2013 x DiverseFACES
The model is only able to consistently categorize happiness and neutral. However, because all other emotions were presumed to be neutral, it may not be that the FER-2013 Model is accurately categorizing neutral, but instead defaulting to neutral as its prediction. The FER-2013 Model incorrectly labels 3 of the faces as surprise, reflecting the fact that none of the faces in the DiverseFACES dataset were expressing surprise.

#### FER-2013 x JAFFE
Here, the model also shows some accuracy in categorizing sadness and surprise as well (although similarly, it completely fails for emotions like fear, anger, and disgust). We see that while there is still a common “default categorization” of faces as neutral, a lot of faces across emotions are being characterized as sadness. 

