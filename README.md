# Self-Driving Car Simulation

This project implements a self-driving car simulation using a convolutional neural network (CNN) trained on driving data to predict steering angles from camera images. The system consists of a Flask-SocketIO server that receives telemetry data (speed and images) and sends back steering and throttle commands.

## Features

- Real-time steering prediction using a pre-trained Keras model
- Image preprocessing pipeline (cropping, color conversion, blurring, resizing)
- Data augmentation for robust training (zoom, pan, brightness adjustment, flipping)
- Dataset balancing to handle steering angle distribution
- NVIDIA-inspired CNN architecture for end-to-end learning
- SocketIO communication for simulation integration

## Prerequisites

- Python 3.7+
- Virtual environment (recommended)

## Installation

1. Clone or download the project repository.

2. Navigate to the project directory:
   ```
   cd c:/Users/Pratham/Documents/carsim
   ```

3. Create and activate a virtual environment:
   ```
   python -m venv venv
   venv\Scripts\activate  # On Windows
   ```

4. Install the required dependencies:
   ```
   pip install -r self drive/requirements.txt
   ```

5. Extract the training data (if not already done):
   - The `data.zip` file contains the driving dataset used for training.
   - Extract it to create the `data/` directory with images and driving log.

## Usage

### Running the Simulation Server

1. Ensure the trained model is present at `self drive/model/model.h5`.

2. Run the server:
   ```
   python self drive/drive.py
   ```

3. The server will start on port 4567 and listen for telemetry data.

4. Connect your driving simulator (e.g., Udacity's self-driving car simulator) to `localhost:4567`.

5. The server will receive camera images and speed data, predict steering angles, and send control commands back.

### Training the Model

Use the provided Jupyter notebook `Self_Driving_Car.ipynb` to train the model:

1. Open the notebook in Jupyter or Google Colab.

2. Follow the cells to:
   - Extract and load the driving data
   - Balance the dataset
   - Apply data augmentations
   - Train the NVIDIA model architecture
   - Save the trained model as `model.h5`

3. Move the saved `model.h5` to the `self drive/model/` directory.

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

