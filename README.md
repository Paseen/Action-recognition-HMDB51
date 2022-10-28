I'll update the readme very soooooooon :) sorry for the waiting

In the meantime you can read the [Report](https://github.com/Paseen/Action-recognition-HMDB51/blob/main/Report.pdf) which shows the job me and my colleagues did 


# Action recognition on HMDB51 dataset using deep neural networks
In this project we used a two-stream CNN to perform an action recognition task on HMDB-51 dataset. The two-stream CNN is composed by a spatial CNN that elaborates video's frames and by a temporal CNN that elaborates the video's optical flows. After the convolutions the two streams were joined by averaging the CNN's softmax scores. 
<br><br>
We build two neural networks that differ only by the spatial CNN: the first one has an hand-crafted architecture, the second one is a finetuned ResNet50. 

# Frames and optical flow extraction

In order for the spacial and temporal networks to work all the franes and optical flows from whe whole set of videos in the dataset have been extracted.

# Data augmentation

The extracted data underwent a data augmentation process which consisted in random cropping and flipping of the frames or optical flows. This was done in order to increase the number of informations that the model would have used for its training.
<br>
Finally the images have been resized to a 224x224 shape, which was the input dimension for both CNNs.  

# Training and test set
The training and test set division was the same as the one suggested by the creators of the dataset; the division was done in order to maximization the relative proportion balance of the videos meta tags. For each of the 51 classes 70 training and 30 testing videos were drawn.  

# Training phase 

- Spatial CNN: for the finetuning of the ResNet50 we added a layer of fully connected neurons after the pretrained CNN architecture and trained only this last section. The training was done by giving to the model 17 equally distanciated frames from each videos of the training set   

- Temporal CNN: the net was trained with a 128 size batch at a time. This batch was composed by 128 optical flows drawn from random videos. The optical flows were made by a stack of 10 consecutive x-channel and 10 consecutive y-channel optical flows from the same time interval of the video. The resulting input was a stacked optical flow with a 224x224x20 shape. 

# Testing phase



# Results
|Network     | One frame | Whole video  |
-------------|:--------------:|:----:|
|Spatial ResNet-50     |39.0%           |45.0% |
|Temporal    |25.8%           |NA% |
|Fusion      |38.0%           |NA% |



(devo sistemare notebook expl)

