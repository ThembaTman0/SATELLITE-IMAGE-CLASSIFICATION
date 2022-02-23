# SATELLITE-IMAGE-CLASSIFICATION
![](img/google-earth-view-7023.jpg?raw=true "")
This image is acquire from [Earth View By google maps](https://earthview.withgoogle.com/)
</br> </br> 
Advancements in remote sensing techniques provide crucial information for a
variety of applications, including landscape changes, land cover categorization, enhanced weather forecasting, and climate observation. These satellite
devices can detect hazardous or dangerous conditions without endangering
people or equipment. With the recent breakthroughs that have made satellites both more powerful and cheaper to deploy, the volume of high-resolution satellite images collected has increased exponentially. Manual classification techniques of these
high-resolution satellite images are too inaccurate and inefficient to handle
the challenge. Hence, automation of satellite image classification has become a crucial part of the field of remote sensing.
</br> </br> 
The main objective of the research paper is to create an efficient, and reliable
autonomous classification models using the bag of features method on the
UC Merced landuse dataset, and improve the accuracy and overall effectiveness of the algorithm proposed by [[2]](https://arxiv.org/abs/1702.06850) mainly for object recognition in satellite imagery. A summary of the report can be found [here](RESEARCH_SUMMARY.pdf)

## Models and Accuracy:
Models  | Accuracy
------------- | -------------
Hybrid Classifier  |  81.42%
KNN  |  68.02%
Linear Classifier  | 76.19%
HOG only  | 36.73%
DAISY only |  73.40%
## Confusion Matrix:
Daisy Classifier
</br> </br> 
![](img/Daisy-Classifier.png?raw=true "")
</br> </br> 
Hybrid Classifier
</br> </br> 
![](img/Hybrid-Classifier.png?raw=true "")
</br> </br> 
Linear Classifier
</br> </br> 
![](img/Linear-Classifier.png?raw=true "")


