# Computer-Vision-Lip-Reading-2.0
Why "2.0"? This project builds upon one of my past projects where I attempted to create a solution to the same problem but using a vastly different strategy. Visit my old project [here](https://github.com/allenye66/Computer-Vision-Lip-Reading).


### Read the paper for my project [here](https://docs.google.com/document/d/1FLVwjXf4BfxgjIBl9CszCMwwwQ-Tm0crAv71qGPmLCM/edit)!


## Synopsys

The goal of this project is to build a speech recognition system that can accurately recognize spoken words from a set of pre-defined words. The algorithm used to recognize words uses computer vision + deep learning and is trained on a large dataset generated by myself and a friend. The dataset consists of around 700 individual video clips (can be found in the ```/outputs/``` folder), totaling approximately 3 GB of data. The model architecture includes several convolutional and dense layers, and was trained using TensorFlow and Keras. The training process achieved a 95.7% training accuracy and a 98.5% validation accuracy, demonstrating strong classification performance. Once trained, the system can be used to recognize spoken commands in a live setting.

## Training Data

Since a suitable dataset was not available for this problem, I took the initiative to create my own dataset by collecting approximately 700 video clips of words being spoken. Each video clip was manually labeled with a word from a predefined set and in the end, I had around 3 gigabytes worth of total data.

<div style="display: flex;">
  <img src="https://user-images.githubusercontent.com/46653284/230745100-da996aaf-f743-4363-b715-6e2ee41493b4.gif" alt="gif 1" >
  <img src="https://user-images.githubusercontent.com/46653284/230745107-2c7c3282-183a-49c7-ad1e-507eb4a2493d.gif" alt="gif 2" >
  <img src="https://user-images.githubusercontent.com/46653284/230745108-70e30408-e504-4d1b-8dbc-2f51be5b39ec.gif" alt="gif 3">
  <img src="https://user-images.githubusercontent.com/46653284/230745525-236348de-c8d4-4bef-94b8-1709513500e8.gif" alt="gif 4">
</div>


## Demo

https://user-images.githubusercontent.com/46653284/228344036-ad19e45c-d329-4040-9e05-ef3bca7b3e50.mov



## Files/Folders

- `writeup.pdf`: a detailed documentation of my entire project. To view the gifs, please visit [here](https://docs.google.com/document/d/1FLVwjXf4BfxgjIBl9CszCMwwwQ-Tm0crAv71qGPmLCM/edit).

- `/data/collect.py`: This script is used to collect the data for training the speech recognition model. It records audio clips of people speaking the different commands and saves them to a directory.

- `/training/3DCNN.ipynb`: This Jupyter Notebook contains the code used to train the speech recognition model. It uses a 3D convolutional neural network to extract features from the audio clips and then classifies them using a softmax layer.

- `/demo/predict_live.py`: This script can be used to test the trained speech recognition model in a live demo. It records audio from a microphone, feeds it into the model, and returns the predicted command.

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

## Dependencies

The following Python packages required to run the scripts can be found in ```requirements.txt```.


## Note

To use the live prediction script `/demo/predict_live.py`, please note that it may not work on all systems. You may need to modify the script to work with your specific setup, including having the same operating system and webcam as the one used during training.




