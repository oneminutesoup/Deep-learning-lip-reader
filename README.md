# Deep-learning-lip-reader

![demo](https://github.com/user-attachments/assets/c0323f94-9992-42c2-a4f4-6d0765e6e407)

## Project Overview

Read the academic paper here for a more in-depth explanation [here](https://docs.google.com/document/d/1wcgc2VE5HnOLy8nQ6LmYVnoI-_koHmark5gJUKDQPj4/edit)!

What is the point of DL-lip-reader? This project aims to create a speech recognition system capable of accurately identifying spoken words from a predefined set. The system leverages computer vision and deep learning techniques and is trained on a custom dataset generated by myself and a friend. The model has been successful with a training accuracy of 96.8% and a real-time testing accuracy of 98.9%, reflecting its effectiveness in word classification. Given enough data, the system is capable of recognizing spoken commands in real-time.
## Training Data

Due to the lack of an existing dataset that met the requirements, a custom dataset was created by collecting approximately 600 individual videos of spoken words. Database was ~2.2 GB in size after finalization

![Untitled video - Made with Clipchamp (3)](https://github.com/user-attachments/assets/d0845600-0920-4fb7-8cb2-d2db7cb9990b)

**Data Collection Process:**

1. **Detect Speaking**:
   - Monitor speech by checking if the distance between the upper and lower lips exceeds a predefined threshold.
   
2. **Record Frames**:
   - Start capturing frames when speech is detected.
   - Users may close their mouths intermittently. If lips remain closed for too long, it is assumed that speaking has stopped.
   
3. **Finalize Recording**:
   - Stop capturing frames once speech has ceased.
   - Add "previous" and "after" frames to the recorded sequence:
     - **Previous Frames**: Frames stored before recording began.
     - **After Frames**: Continuously added frames to reach a total of 22 frames.
   - Save all frames in a NumPy array and export them to a text file.

## Files/Folders

- `writeup.pdf`: a detailed documentation of my entire project.

- `/data_collection/collect.py`: This script is used to collect the data for training the speech recognition model. It records audio clips of people speaking the different commands and saves them to a directory.

- `/demo/predict_live.py`: This script can be used to test my trained speech recognition model in a live demo. It uses similar logic from the data collection script by collecting frames, feeding it into the model, and then displays the predicted command.

- `/model/`: contains various model weights for trained models.

- `/demo_examples/`: mp4 files containing recorded demos of my model predicting words that I spoke in real-time.


## Usage

To use my project, please read the following:

1. Run `collect.py` to record audio clips of yourself speaking a chosen word and save them to a directory.
    - First, enter the word you want to collect data for.
    - If this is your first time running the script, do not enter a lip distance (it will calibrate itself).
2. Use `predict_live.py` to test the trained model in a live demo.
   
## Challenges Encountered

During the development of this project, several technical challenges were encountered:

1. **Dataset Creation**:
   - Constructing a high-quality, diverse dataset involved a *ridiculous* amount of time to complete. Ensuring consistency in video recording conditions and accurately labeling each clip presented difficulties, affecting the overall reliability of the training data.

2. **Processing Power Limitations**:
   - Training the model required substantial computational resources, which was difficult to manage as I was often bottlenecked by my NVIDIA 3060TI. The optimization of hyperparameters, such as learning rates and batch sizes, demanded multiple iterations. Achieving convergence and preventing overfitting necessitated careful tuning and the use of regularization techniques.

3. **Real-time Inference**:
   - Achieving efficient real-time performance while maintaining high accuracy was challenging. The model's inference speed and latency were critical, requiring optimization of the model architecture and processing pipeline to handle live inputs effectively.

## Future Improvements

To enhance the project and address the identified challenges, the following technical improvements are proposed:

1. **Dataset Augmentation**:
   - Expand the dataset by incorporating a greater number of video samples with varied environmental conditions and speaker demographics. Techniques such as data augmentation and synthetic data generation could further enhance dataset diversity and model robustness.

3. **Inference Optimization**:
   - Optimize the inference pipeline by leveraging model quantization, pruning, or deploying the model on specialized hardware accelerators like GPUs or TPUs to reduce latency and improve real-time responsiveness.

4. **User Interface Development**:
   - Develop a graphical user interface (GUI) to facilitate user interaction and visualization of model predictions. Implementing an intuitive GUI with real-time feedback could enhance user experience and accessibility.

5. **Multilingual and Multimodal Support**:
   - Extend the system to support multiple languages and dialects. Incorporate multimodal inputs, such as audio alongside video, to improve recognition accuracy and adaptability across different linguistic contexts.
