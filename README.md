Project Name: 
Hand Detection Shredder Machine.

Problem Statement:
Objective here is to build an application that can effectively detect hands on shredder machine and raise alarm as soon as hand crosses safety line.
Also,shredder machine will shut off if hands further crosses border line. This help prevent accidents on shredder machine which in past have caused many 
operators severe injuries.

![img1](https://user-images.githubusercontent.com/58501212/151506706-d2f0160b-5004-4d04-9579-9b1236554e9b.jpg)


Tech Stack:

Python 3.6
Deep learning framework --- Tensorflow 1.14 --TFOD 1.14
Image processing library -- opencv/imutils


Data Collection:

Data needed to train model for detecting hands was collected from industry site. Camera was installed that captured ~5k images of hands in different 
lighting conditions, with and without gloves.
Also, some palm/hands images matching criteria were scrapped from web to make trained model general.

Pre-Processing:
During pre-processing below operations were done:

1.) Data Agumentation -- Using Agumentor Image Rotating,flipping,cropping,Random Brightness/contrast/colour/erasing and zooming were done 
2.) Resizing  -- As images were of different sizes, all were resized to same size.
3.) Splitting -- 5k images were splitted into training,valid and Test set in ratio of 70,15,15


Data Annotation:

Data Annotation was done for Training and Validations et labelimg tool.
This cerates a xml file corresponding to each jpg file. Xml file have class,xmin,xmax,ymin,ymax(box co-ordinates)
These xml files were converted to csv (XML to CSV conversion). Now, each image is a CSV record but we need each image as tensor record.
Hence,each csv record is converted to tensor.


Model Training:
We trained custom images on couple of models from Tensorflow model ZOO (Refer Training file:Training_model.ipynb)
https://github.com/tensorflow/models/blob/v1.13.0/research/object_detection/g3doc/detection_model_zoo.md

1.) faster_rcnn_incpetion_v2_coco
2.) ssd_mobilenet_v2_coco
3.) ssdlite_mobilenet_v2_coco


Important config files:
1. Labelmap.txt 
2. Model Configuration
3. Frozen Infeence Graph

Model is trained and Frozen_Inference_Graph.pb file is generated (This file have trained model).


## Creating Application
Below are main components in ShredderSystem application:

•	Taking live feed from camera and capturing frames.
•	Detecting palm in each frame.
•	Creating Safety and Border lines in frame/ distance of palm from safety line.
•	Capturing Alert if hand crosses safety line and generating Alarm.
•	Shutting off shredder machine if hand crosses border line (Raspberry PI micro-controller and Relays are used here to control shredder machine)
•	Logging all records
•	Turning on Shredder machine as hand goes behind border line.


![image](https://user-images.githubusercontent.com/58501212/151506784-235279d7-67eb-4882-97e6-90660c469ad8.png)

