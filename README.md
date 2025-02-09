# Driver Drowsiness Detection System
![image](https://github.com/user-attachments/assets/eb6a3ab7-1c3a-4529-a7df-4a5bb8b68122)
## Overview

Driver fatigue is a significant contributor to road accidents worldwide. This project presents a real-time Driver Drowsiness Detection System leveraging Deep Learning (CNNs) and Computer Vision (OpenCV) to monitor a driver's eye status and issue an alert if signs of drowsiness are detected.

The system continuously captures frames from a webcam, detects the driver's face and eyes, classifies the eyes as "Open" or "Closed" using a Convolutional Neural Network (CNN) model, and triggers an alarm if the driver appears drowsy for a prolonged period.

## Key Features

- **Real-time Face and Eye Detection** using Haar Cascade classifiers.
- **Deep Learning-based Eye State Classification** with a trained CNN model.
- **Drowsiness Scoring System** to determine fatigue levels over time.
- **Audible Alarm** to alert the driver in case of drowsiness detection.

## System Architecture

1. **Image Capture:** Continuously captures video frames from the webcam.
2. **Face and Eye Detection:** Uses Haar Cascade classifiers to localize the face and eyes.
3. **Eye Classification:** Feeds detected eye images into a trained CNN model to classify them as "Open" or "Closed."
4. **Drowsiness Detection:** Computes a score based on eye closure duration.
5. **Alert Mechanism:** If the score exceeds a predefined threshold, the system plays an alarm sound.

## CNN Model Architecture

The Convolutional Neural Network (CNN) used for eye classification consists of:

### Convolutional Layers:
- Conv2D (32 filters, kernel size 3x3) + ReLU
- Conv2D (32 filters, kernel size 3x3) + ReLU
- Conv2D (64 filters, kernel size 3x3) + ReLU

### Pooling Layers:
- MaxPooling2D (pool size 1x1) after each convolutional layer

### Dropout Layers:
- To prevent overfitting

### Fully Connected Layers:
- Dense (128 neurons, ReLU activation)
- **Output Layer:** 2 neurons (Softmax activation for classification: 'Open' or 'Closed')

## Dependencies

Ensure Python (version 3.6 or later) is installed. Install the required libraries using:

```bash
pip install opencv-python tensorflow keras pygame numpy
```

## Project Files

- **Haar Cascade Files (`haar cascade files/`)**: XML files for detecting faces and eyes.
- **CNN Model File (`models/cnnCat2.h5`)**: Pretrained model for eye classification.
- **Alarm Sound (`alarm.wav`)**: Audio alert triggered upon drowsiness detection.
- **Python Scripts:**
  - `Model.py`: Defines and trains the CNN model.
  - `Drowsiness_Detection.py`: Main script executing the detection system.

## How It Works

### Step 1 – Image Capture
- The webcam captures frames using `cv2.VideoCapture(0)`.
- Frames are converted to grayscale for efficient processing.

### Step 2 – Face & Eye Detection
- Haar Cascade classifiers detect the face and eyes in each frame.
- The detected eye regions are extracted as Regions of Interest (ROI).

### Step 3 – Eye Classification
- Eye images are resized to 24x24 pixels, normalized, and fed into the CNN model.
- The model classifies each eye as either Open or Closed.

### Step 4 – Drowsiness Detection
- If both eyes are closed for consecutive frames, the system increases a drowsiness score.
- When the score surpasses a threshold, the alarm is triggered via the Pygame library.

## Running the System

Navigate to the project directory and execute:

```bash
python Drowsiness_Detection.py
```

The system will start monitoring the driver in real-time and raise an alert if drowsiness is detected.

## Future Enhancements

- **Improve Model Accuracy:** Train on a larger dataset with more diverse lighting and facial conditions.
- **Multi-person Monitoring:** Extend support for detecting multiple drivers in fleet vehicles.
- **Additional Drowsiness Indicators:** Integrate head pose estimation and yawning detection.
- **Mobile Integration:** Develop an Android/iOS app for portable use.

## Contributions

We welcome contributions to enhance this project. Please submit issues or pull requests via GitHub. For significant changes, open an issue first to discuss improvements.

## References

- [OpenCV Documentation](https://opencv.org/)
- [Keras Documentation](https://keras.io/)
- [TensorFlow Documentation](https://www.tensorflow.org/)

This project presents a highly scalable and impactful application of AI in transportation safety, helping mitigate fatigue-related accidents through real-time monitoring. 🚗💡
