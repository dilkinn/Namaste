# Using Computer Vision and Transfer Learning to Classify Yoga Poses

Here is the link to my presentation slides: https://docs.google.com/presentation/d/1u6QkRlfu72sQDPaxyLaqZl_52xW-Sj13buVQwVe6scs/edit?usp=drive_web&ouid=118087232464696496278

Yoga is great for both physical and mental health. There's no challenging aspect in yoga, everyone can practice at it's one paste. What important in the path, not the goal. 

Despite I have been practicing yoga for 10 years, I cannot memorize sanskrit yoga poses names and I can only name couple of those. I can bet I am not the only one.

The tricky part here: you need to know the yoga pose name to look it up in the internet.
I wanted a way to discover a yoga pose name based on the picture I have. I can do a pose, I want to know it's name.

As a possible unraveling of the project, I see the following:
  - Safety control while practicing at home: straight back check, sholders down check and so on
  - Vinyasa sequence decoder.

I built a deep learning classifier based on Convolutional Neural Network (CNN) and compare approaches:
  - model trained solely on the train dataset
  - transfer learning model

## Data Sources

I train my models on a dataset which contained 11 classes: 10 yoga poses and 1 non-yoga poses.
  1 Bridge - Setu Bandha
  2 Childs - Balasana
  3 Downward Dog - Adho Mukha Shvanasana
  4 Mountain - Tadasana
  5 Not a yoga pose
  6 Plank - Phalakasana
  7 Seated Forward Bend  - Paschimottanasana
  8 Tree - Vrikshasana
  9 Warrior 1 - Virabhadrasana 1
  10 Warrior 2 - Virabhadrasana 2
  11 Triangle  - 
  
Training dataset included 100 images for each class. 
Most images in the training dataset were made on white background by people wearing contrast clothes.
Pictures represented a photographs taken from different angles and with varying zoom.

<div align="center">
      <img height="300" src="images/schema-system.png">
</div>

I got two test sets:
  1 Yoga poses that resemble train data set style, i.e. white background and contrast clothes.
  2 Images of yoga poses taken by real people not necessarily on white background.
  
## Models Description

The dataset of 100 images per class is relatively small dataset. Therefore I have applied the data augmentation by 
  - shearing
  - zooming
  - horizontal flipping
  - rotating
  - width and height shifting
  
### CNN from scratch

Below is the architechture of the 'from-scratch' CNN:
<div align="center">
      <img height="300" src="images/architecture_scratch.png">
</div>

Model training accuracy for training and validataion data with respect to the number of epochs:
<div align="center">
      <img height="300" src="images/acc_scratch.png">
</div>

### Transfer learning
Below is the architechture of the 'transfer learning' CNN:
<div align="center">
      <img height="300" src="images/architecture_transfer.png">
</div>

Model training accuracy for training and validataion data with respect to the number of epochs:
<div align="center">
      <img height="300" src="images/acc_transfer.png">
</div>

"Transfer learning" convolutional network shows better performance on validation data: 71% accuracy versus 58% for the "from scratch" model. 

## Results

Here is the performance of the "transfer learning" model on the test data.

Google search test: 0.74
GalvanizeNYC12 cohort test: 0.58

The confusion matrices indicate that the model is confused with "triangular poses". For example Warrior 1 and Warrior 2 look very similar and mainly differ with hands position and upper body rotation. Triangle pose and bridge also can look similar  Warrior 1 and 2 poses. 

<div align="center">
      <img height="300" src="images/acc_transfer.png">
</div>

## Conclusion
 - The "from scratch" model works slightly worse that the "transfer learning" VGG19 model
 - Confusion matrices show that "triangular" poses are confused the most

## Future Deriction
Model improvement strategies:
  - Training dataset increase
  - Separate training for triangular, standing, siffing poses
  - Increase the number of poses/classes
  
Future use cases:
  - Yoga pose name application (upload a photo, get the pose name)
  - Safety control for home practice
