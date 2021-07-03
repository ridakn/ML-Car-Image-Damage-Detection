# ML-Car-Image-Damage-Detection
Using machine learning model Mask R-CNN to detect damage in car images

## Objective

<p align = "justify">
Create and application using ML that takes an image of a car (or some part of a car) and is able to recognise if the car is damaged or not. This damage can be a scratch or a dent. The image is processed using OpenCV techniques and then fed as input into the network. Ideally, the network outputs an image with the damaged part outlined. </p>

## Network Used

<p align = "justify">
A Mask R-CNN is used for detecting the damage. Mask R-CNN uses instance segmentation which means segmenting individual objects within a scene regardless of their type i.e. each object is segmented as an individual object even if there are multiple types of it in the scene. For our project, this means each damage will be segmented as a separate segmentation in the case there are multiple damaged parts on a car. Mask R-CNN has been trained on the COCO dataset and is able to segment objects by identifying their pixel locations. In addition to identifying the object and drawing a shape around it, it also colours pixels in that shape to correspond to that object (or class). Mask R-CNN is a combination of Fast R-CNN which does object detection and Fully Convolutional Network which creates the pixel wise boundary. </p>
  
## Training

<p align = "justify">
The training set for our project is a collection of car images which have damage on them. These can be images of any damaged part of the car from any side. The damage can be a scratch or a dent and both are classified as one class: 'damage'. To create our training images, we use the VGG annotator to create shapes around the damaged area. The pretrained Mask R-CNN was used for training on the car images for 10 epochs. </p>

<img width="994" alt="Screen Shot 2021-07-04 at 12 32 16 AM" src="https://user-images.githubusercontent.com/32781544/124366265-57bdc800-dc03-11eb-8c1d-8a2aa70fa7ea.png">

## VGG Annotator

<p align = "justify">
The VGG annotator is an open source project which can be used to define regions in an image and create textual description of those regions. This can be used for supervised learning. We use this annotator to define a region called 'damage' in the car images and the information i.e. the image name and the coordinates of the region along with the class name are saved in a JSON file. Sample images with the defined regions are shown below.  </p>

## Testing

<p align = "justify">
Testing was done on car images and the results can be seen below. It was mostly successful on images that were part of the training set. On non-training images, it wasn't able to recognise the damage when it wasn't a stark difference in colour of the pixels. </p>

<img width="962" alt="Screen Shot 2021-07-04 at 12 32 46 AM" src="https://user-images.githubusercontent.com/32781544/124366271-5ee4d600-dc03-11eb-87a6-6e5f44ce8ade.png">
<img width="850" alt="Screen Shot 2021-07-04 at 12 33 04 AM" src="https://user-images.githubusercontent.com/32781544/124366275-60ae9980-dc03-11eb-9a0f-568bc84efcea.png">

