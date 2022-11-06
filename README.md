# Hard Hat/Head Detection using YOLOv5

## Build a Personal Safety Equipment Detection System


In this project, I have built an object detector for the given Hard Hat/ head detection dataset.

### Model Used:

#### YOLOv5: 

The YOLO model was the first object detector to connect the procedure of predicting bounding boxes with class labels in an end to end differentiable network.

 

The YOLO network consists of three main pieces.

1) __Backbone__ - A convolutional neural network that aggregates and forms image features at different granularities.

2) __Neck__ - A series of layers to mix and combine image features to pass them forward to prediction.

3) __Head__ - Consumes features from the neck and takes box and class prediction steps.

There are many approaches one can take to combining different architectures at each major component. The contributions of YOLOv4 and YOLOv5 are foremost to integrate breakthroughs in other areas of computer vision and prove that as a collection, they improve YOLO object detection.

### Training Procedures

__Data Augmentation__ - Data augmentation makes transformations to the base training data to expose the model to a wider range of semantic variation than the training set in isolation.

__Loss Calculations__ - YOLO calculates a total loss function from constituent loss functions - GIoU, obj, and class losses. These can be carefully constructed to maximize the objective of mean average precision.

—------------------------------------------------------------------------------------

### Stage 1:

●	In stage 1, I trained the model on the given hard_hat/head  dataset.

●	As yolo takes the annotations in .txt format, I selected equal ratios of hard_hat/head images(48 images for training and 18 for validation) from the given dataset and annotated them using LabelImg.

●	Then I trained the YOLOv5 model( which was pre-trained on coco dataset) with my dataset and runned it for various combinations of batch sizes and epochs.

●	The best results were obtained with 400 Epochs with Batch Size = 4. 

●	The mAP (mean average precision) for Head: 0.949 (94.9%).

●	The mAP (mean average precision) for Helmet: 0.830 (83.0%).

●	After that I did the inference on the given video and found promising detections.

●	Stage 1 video link: [Stage 1 Output Video](https://drive.google.com/file/d/1mFufIUgjc3PMlS96Wo7Df3Y82WJ5d2YK/view?usp=sharing).

![hard_hat_workers182](https://user-images.githubusercontent.com/57324641/200188664-6b390640-9bde-4d37-8af2-43990e4cd3be.png)
![hard_hat_workers43](https://user-images.githubusercontent.com/57324641/200188715-2798d7f3-9f5c-4f34-bd0f-3fefbf19f5f1.png)




### Stage 2:

●	For this stage, I changed the color of the bounding boxes according to the color of the hat.

●	For this I have gone through two different files which were present in the YOLOv5 model namely, detect.py and plots.py.

●	In detect.py, I wrote some lines of code which will first create an object of the source image and then save the bounding box coordinates (xmin, ymin, xmax, ymax) of the two tuple variables p1 and p2.

●	Further calculated the center coordinates, shifted the y-coordinate a little above(the pixel will direct to the helmet) and using the getpixel() function, read the RGB values of that particular pixel. Passed the ‘col’ variable in annotator.box_label().

![Screenshot 2021-12-28 133903](https://user-images.githubusercontent.com/57324641/200192007-4caf5649-28d8-44f3-99f8-c3c8dcff2f40.png)

●	Further in plots.py, in the box_label function, two methods were defined to create the box labels. Since PIL uses RGB format only, no changes have to be made there(if section). But CV2 uses BGR format so there in the else section I just reversed the color tuple variable.

![Screenshot 2021-12-28 133755](https://user-images.githubusercontent.com/57324641/200192027-bcbe6570-def8-4e0e-ba74-6e99682e62f3.png)

●	With this I was able to achieve the colored bounding boxes according to the helmet color.

●	These images are also present in the Stage 2 folder.

![Stage2_Output1](https://user-images.githubusercontent.com/57324641/200188763-8f13b1e6-0e35-4ccf-a60d-0b9af67f191a.png)
![Stage2_Output2](https://user-images.githubusercontent.com/57324641/200188767-e7b1989a-6682-4f08-b966-1cc18b8deaef.png)



### Sample Outputs:

●	I have shared the 

    ○	Test images along with the predictions. (Test_Images)
    
    ○	Zip file containing the annotations in .TXT format. (Annotations(.TXT Format).zip)

●	It contains all the detections of the hard hat helmet and head.

● YOLOv5 Model Link: [YOLOv5 Model](https://drive.google.com/file/d/1TdwY5X3seEkvwesFreoLVgPOxcY1V4aA/view?usp=share_link)
