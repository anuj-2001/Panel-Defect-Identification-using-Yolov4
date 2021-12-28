# Panel-Defect-Identification-using-Computer-Vision


Google colab code link : https://colab.research.google.com/drive/1qffw1ztI5otaznY-GqQADWcchAuOPTjR?usp=sharing

Google Drive Link of the Assignment and Resultant Video : 
https://drive.google.com/drive/folders/1uAhb4r_lpovpGNu4Q-su7U_m2YBbpfEw?usp=sharing


STEP 1 : Train-Test Split

First thing I did is split the dataset into training and testing data. I chose first 7 videos for training data and the last one for testing data.


STEP 2 : Extraction of frames from training data

As the training data obtained was in mp4 format, next I extracted frames out of all the videos and saved it into a folder.

STEP 3 : Dataset Labelling

I was given two classes : Panel and Defect. In order to label the obtained frames, I used https://github.com/tzutalin/labelImg for labelling. I labelled every frame manually by identifying the panel portion and defect portion.

STEP 4 : Darknet and Yolov4 Setup and Training

I created a new Google Collab file and cloned and built the darknet repository into it. I also made a prediction to check the working of Yolov4. Then I split some part of my train data to validation data (I had a total of 49 extracted frames out of which I used 41 for training and 8 for validation), converted both of them into zip files and uploaded on the drive. I also uploaded the data and names files accordingly. I took the cfg file from the darknet repository and made some changes respectively : 
 Set the width and height to 416 each.
Set the max_batches to 6000.
Set the steps to 4500, 5400 respectively.
Changed the number of filters to 21 and the number of classes to 2(Panel and Defect).
Thereafter I performed training on the dataset on the pre trained yolov4 weights for the convolutional layers(Training took a lot of time as it was for 6000 batches, so I had to stop at around 500 batches where I analyzed the avg loss to be in acceptable ranges). After training I saved the newly trained yolov4 weights in my google drive.

STEP 5 : Testing the obtained results

I converted the obtained yolov4 weights to a tensorflow model, which would predict the final detections on any given input image or video and count the number of objects too.
