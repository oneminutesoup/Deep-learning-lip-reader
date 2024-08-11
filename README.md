# Deep-learning-lip-reader

## Demo

https://user-images.githubusercontent.com/46653284/228344036-ad19e45c-d329-4040-9e05-ef3bca7b3e50.mov

### Read the paper for my project [here](https://docs.google.com/document/d/1FLVwjXf4BfxgjIBl9CszCMwwwQ-Tm0crAv71qGPmLCM/edit)!

### View some demos [here](https://www.youtube.com/watch?v=E6bSWkDdcQM), [here](https://www.youtube.com/watch?v=RDC2C3MRoEU&feature=youtu.be), and [here](https://www.youtube.com/watch?v=6S--eCpAwHk).

## Project Overview

What is the point of DL-lip-reader? This project aims to create a speech recognition system capable of accurately identifying spoken words from a predefined set. The system leverages computer vision and deep learning techniques and is trained on a custom dataset generated by myself and my friend. The model has been succesful with a training accuracy of 96.8% and a real-time testing accuracy of 98.9%, reflecting its effectiveness in word classification. Given enough data, the system is capable of recognizing spoken commands in real-time.
## Training Data

Since a suitable dataset was not available for this problem, I took the initiative to create my own dataset by collecting approximately 700 video clips of words being spoken. Each video clip was manually labeled with a word from a predefined set and in the end, I had around 3 gigabytes worth of total data.

How does my `/data_collection/collect.py` script work? 
- First detect if someone is talking (based upon if the distance between the upper lip and lower lip is greater than a threshold)
- If someone is talking:
  - Start "recording" or storing the current frames
  - The user can close their mouths for some short periods of time, but if they close their lips for too many frames then the script assumes they have finished talking.
  - Once the user finishes talking, we stop saving frames and then pad the current saved frames with "previous" and "after" frames
    - "previous" frames are frames stored (in a circular buffer) before we started saving frames
    - "after" frames are just continously added until we reach 22 frames (a predefined constant)
  - all 22 frames are stored in a numpy array and written to a text file (we also record the frames as images and turn those into a video file)

Example outputs:
<div style="display: flex;">
  <img src="https://user-images.githubusercontent.com/46653284/230745100-da996aaf-f743-4363-b715-6e2ee41493b4.gif" alt="gif 1" >
  <img src="https://user-images.githubusercontent.com/46653284/230745107-2c7c3282-183a-49c7-ad1e-507eb4a2493d.gif" alt="gif 2" >
  <img src="https://user-images.githubusercontent.com/46653284/230745108-70e30408-e504-4d1b-8dbc-2f51be5b39ec.gif" alt="gif 3">
  <img src="https://user-images.githubusercontent.com/46653284/230745525-236348de-c8d4-4bef-94b8-1709513500e8.gif" alt="gif 4">
</div>

## Files/Folders

- `writeup.pdf`: a detailed documentation of my entire project. To view the gifs, please visit [here](https://docs.google.com/document/d/1FLVwjXf4BfxgjIBl9CszCMwwwQ-Tm0crAv71qGPmLCM/edit).

- `/data_collection/collect.py`: This script is used to collect the data for training the speech recognition model. It records audio clips of people speaking the different commands and saves them to a directory.

- `/training/3DCNN.ipynb`: This Jupyter Notebook contains the code used to train the speech recognition model. It uses a 3D convolutional neural network to extract features from the audio clips and then classifies them using a softmax layer.

- `/demo/predict_live.py`: This script can be used to test my trained speech recognition model in a live demo. It uses similar logic from the data collection script by collecting frames, feeding it into the model, and then displays the predicted command.

- `/model/`: contains various model weights for trained models.

- `/demo_examples/`: mp4 files containing recorded demos of my model predicting words that I spoke in real-time.


## Usage

To use my project, please read the following:

1. Run `collect.py` to record audio clips of yourself speaking a chosen word and save them to a directory.
    - First, enter the word you want to collect data for.
    - If this is your first time running the script, do not enter a lip distance (it will calibrate itself).
2. View `/training/3DCNN.ipynb` to see how I trained the speech recognition model on my collected data.
3. Use `predict_live.py` to test the trained model in a live demo. 

Note: The current model implemented in `predict_live.py` is a less accurate model. I am unable to upload the weights for the model showcased in `/training/3DCNN.ipynb` as the file is too large.

## Note

To use the live prediction script `/demo/predict_live.py`, please note that it may not work on all systems. You may need to modify the script to work with your specific setup, including having the same operating system and webcam as the one used during training.




