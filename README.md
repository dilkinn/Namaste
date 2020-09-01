# Using Computer Vision and Transfer Learning to Classify Yoga Poses

I have been practicing yoga for 10 years, and I had difficult times memorizing sanskrit yoga poses names.
The tricky part is that I could only look up the poses, which names I already know, because google search work that way.
I wanted a way to discover a yoga pose name based on the picture I have.

I built a classifier based on Convolutional Neural Network (CNN) and used 2 approaches:
  - CNN from scratch
  - CNN built using transfer learning

## Data sourse

I train my models on a dataset which contained 11 classes: 10 yoga poses and 1 non-yoga poses.
Training dataset included 100 images for each class. 
Most images in the training dataset were made on white background by people wearing contrast clothes.
Pictures represented a photographs taken from different angles and with varying zoom.

<div align="center">
      <img height="300" src="images/schema-system.png">
</div>

I got two test sets:
  1 Yoga poses that resemble train data set style, i.e. white background and contrast clothes.
  2 Images of yoga poses taken by real people not necessarily on white background.
  
## 
