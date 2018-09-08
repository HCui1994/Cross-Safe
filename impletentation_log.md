# Overview
* Instead of manually cut the images into tremendous, very small patches, as what we did before, now the images are sent into a convolutional neural network. Through pooling (down-sampling), the network can generate feature maps of different sizes. Feature map cells are grids on feature maps;
* A feature map cell now can be regarded as a small patch on feature map, but not original image;
With the neural get deeper, the size of feature map gets smaller => multiscale detection.

# Data packing
* Raw data are of format .jpeg and.txt with same filename. Pack all data into Pickle file for faster reading (with images and labels matched). 

# Ground truth encoding
* Encode the ground truth boxes in format of default boxes. A GT box is encoded as [x1_offset, y1_offset, x2_offset, y2_offset] relative to those default boxes who have jaccard (iou) values greater than a threshold with the GT box;
In cross-safe project, GT encoding is done before training as data preprocessing, but not a process during training.

# Training
* Use image size of 300*400 as input;
* The model is built on AlexNet with some additional convolutional layers.
Use AlexNet as base net. This is because most pedestrian lights are “small objects” and the predictions are generated in lower level feature maps. It is tested that the performance is actually the same when using deeper base net, i.e. VGG-19 (test experiments used LISA traffic sign dataset). For faster inferencing, Cross-Safe chooses AlexNet, which has less parameters;
* The feature map sizes are
FM_SIZES = [[36, 48], [17, 23], [9, 12], [5, 6]]
Which means the receptive field of level one feature map cell is approximately 10*10 pixels, level two 20*20 pixels, level three 30*30 pixels and level 60*60 pixels.
* Considering most pedestrian lights have a square shape, 5 different scale square default boxes are selected on each feature map to reduce the number of default boxes and speed up training. This can also help kick out deformed labels, e.g. stipe-like labels, for they tend to have lower jaccard value with default boxes and not selected when training.
