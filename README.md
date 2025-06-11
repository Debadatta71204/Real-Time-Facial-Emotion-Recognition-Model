# Real-Time-Facial-Emotion-Recognition-Model
This project performs facial emotion recognition (FER) using transfer learning with MobileNetV2, trained on a custom version of the FER-2013 dataset. It detects and classifies human emotions from facial expressions captured through images/ web cam

## 🔗 Run in Google Colab

You can try the notebook directly in Colab:

[![Open In Colab]([https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/YOUR_NOTEBOOK_ID_HERE](https://colab.research.google.com/drive/10Gki4xQj2V-2ZQ7u0QJVZ2R1WfkwmTv0?usp=drive_link))

*#Features*

->Uses MobileNetV2 as the base model for transfer learning.

->Trained on custom-upsampled FER-2013 dataset.

->Supports classification into multiple emotions like happy, sad, angry, etc.

->Built with TensorFlow and Keras in Google Colab.

->Training pipeline uses image_dataset_from_directory and prefetching for performance optimization.


*#Current Limitations*

Despite heavy data augmentation and targeted upsampling (especially for underrepresented classes like disgust), the model currently shows bias toward the 'sad' class.

Predictions are often skewed, with a tendency to misclassify happy and neutral images as sad or fearful.

Certain facial expressions like disgust and surprise still suffer from poor precision due to class imbalance and model overfitting.


#Challenges Faced

Here are some of the key obstacles encountered during development:
* Data Imbalance*
Initially, underrepresented emotions like disgust had as few as 436 samples. I manually applied targeted upsampling using data augmentation techniques to improve class balance.
* Model Bias
Despite a balanced dataset, predictions still heavily leaned toward sad or fear. After investigating class weights, image quality, and model architecture, it became clear that transfer learning might not be enough in this context.
* Misclassification Issues
Expressions such as smiling faces were often wrongly predicted as angry or fear, leading to user-visible errors. Debugging involved analyzing individual predictions and cross-verifying image-label pairs.
* Overfitting and Validation Drops
Early models showed sharp drops in validation accuracy compared to training. Implemented callbacks like ReduceLROnPlateau and EarlyStopping to control overfitting.
* Unstable Training Behavior
Due to fluctuations in validation accuracy and loss, the model often required training in bursts rather than long, continuous epochs. I added callbacks like EarlyStopping, ReduceLROnPlateau, and ModelCheckpoint to:
Prevent overfitting
Resume training from best checkpoints
Adjust learning rate when progress plateaued
This helped improve training efficiency and model stability.

*#Current Work-in-Progress*

I'm currently in the process of:

Building a CNN from scratch, tailored specifically for the FER-2013 dataset, instead of relying solely on transfer learning.

Experimenting with custom loss functions and balanced class weights to handle emotion skew.

Adding real-time webcam inference using OpenCV for desktop applications.

*#Technologies Used*

Python

TensorFlow & Keras

OpenCV (for inference, planned)

Google Colab (for training)

Matplotlib & Seaborn (for visualizations)

# Final Thoughts
This project marks my first step into real-world CNN and deep learning applications. While it’s not perfect and still evolving, it represents several months of learning, frustration, debugging, and eventual breakthroughs. I’m actively working to improve the architecture, reduce class bias, and make this model production-ready.

