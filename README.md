# Self-Driving Car Simulation

This project implements a self-driving car simulation using a convolutional neural network (CNN) trained on driving data to predict steering angles from camera images. The system consists of a Flask-SocketIO server that receives telemetry data (speed and images) and sends back steering and throttle commands.

## Features

- Real-time steering prediction using a pre-trained Keras model
- Image preprocessing pipeline (cropping, color conversion, blurring, resizing)
- Data augmentation for robust training (zoom, pan, brightness adjustment, flipping)
- Dataset balancing to handle steering angle distribution
- NVIDIA-inspired CNN architecture for end-to-end learning
- SocketIO communication for simulation integration


## Project Structure

```
carsim/
├── README.md
├── .gitignore
├── Self_Driving_Car.ipynb    # Training notebook
├── data.zip                  # Training data archive
├── 2.mp4                     # Demo video (optional)
├── self drive/
│   ├── drive.py              # Main server script
│   ├── requirements.txt      # Python dependencies
│   └── model/
│       └── model.h5          # Trained Keras model
└── Default Windows desktop 64-bit_Data/  # Ignored simulator data
```

## Model Architecture

The CNN is based on NVIDIA's end-to-end learning architecture:
- 5 convolutional layers with ELU activation
- 3 fully connected layers
- Input: 66x200x3 preprocessed images
- Output: Steering angle prediction

## Data Preprocessing

Images are preprocessed with:
- Cropping to focus on road area (60:135 pixels)
- RGB to YUV color conversion
- Gaussian blur (3x3 kernel)
- Resize to 200x66 pixels
- Normalization to [0,1]

