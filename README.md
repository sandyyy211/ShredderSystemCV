Project Name: 
Hand Detection Shredder Machine.

Problem Statement:
Objective here is to build an application that can effectively detect hands on shredder machine and raise alarm as soon as hand crosses safety line.
Also,shredder machine will shut off if hands further crosses border line. This help prevent accidents on shredder machine which in past have caused many 
operators severe injuries.


Data Collection:

Data needed to train model for detecting hands was collected from industry site. Camera was installed that captured ~5k images of hands in different 
lighting conditions, with and without gloves.
Also, some palm/hands images matching criteria were scrapped from web to make trained model general.

Pre-Processing:
During pre-processing below operations were done:

1.) Data Agumentation -- Using Agumentor Image Rotating,flipping,cropping,Random Brightness/contrast/colour/erasing and zooming were done 
2.) Resizing  -- As images were of different sizes, all were resized to same size.
3.) Splitting -- 5k images were splitted into training,valid and Test set in ratio of 70,15,15


