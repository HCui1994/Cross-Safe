# Cross-Safe
Cross-Safe is a project for real-time pedestrian signal detection and recognition. More specifically, it is based on a deep learning recognition algorithm, enabling robust walking signal sign detection and signal recognition.   
A custom image library was built and developed to train, validate, and test our methodology on real traffic intersections, demonstrating the feasibility of Cross-Safe in providing safe guidance to the visually impaired at urban intersections. 

## Dataset Description
The dataset used contains over 7,000 images collected by volunteers from New York City with Zed camera. Most images contain one pedestrian light located near the center. We manually annotated the images by providing a bounding box and a class label for each traffic light. These images are captured from New York City streets and contain common street scenes like cars, trees, buildings, and pedestrians etc.

## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites
python 3.5  
tensorflow >= 1.4  
matplotlib  
scikit-learn  
jupyter notebook - IPython 

## How to Use
* Clone the repo to somewhere. Refer this folder as `$ROOT`
* Download the Pedestrain Dataset, and store it in a directory `$data`. (Note: both image files and label files live in `$data`. An image file and its corresponding label file shall have a same name).
* Follow the ipython notebook file `cf_data_pack.ipynb` to pack and organize the dataset.
* Follow the ipython notebook file `cf_gt_encode.ipynb` to encode the ground truth labels.
* Follow the ipython notebook file `cf_mdoel.ipynb` to train, test the model. (training and testing configurations are in `config.py`).
* For inferencing, follow the `inference` part in ipython notebook file `cf_mdoel.ipynb`.

## Areas of Improvement
There are multiple potential areas of improvement in this project:
* Now this project can only train the model from scratch. Pre-training the model on VOC dataset may improve the performance.
* Image data augmentation.
* Split the dataset labels to white and red lights.

