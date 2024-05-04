## Tumor Classification and Patient-Friendly Explanation with Deep Learning

### Overview

**Project Goal:** This project integrates a deep learning model that accurately predicts tumor classes from MRI scans with the GEMMA text generation tool. The primary aim is to provide patients with clear, understandable explanations of their MRI results.  
**Accuracy:** The deep learning model demonstrates an impressive accuracy of approximately 97%.

### Model Architecture

- **Convolutional Layers:** Extract meaningful features from MRI images.
  - 4 Convolutional layers with 'relu' activation, increasing feature complexity.
  - MaxPooling layers progressively reduce image dimensionality.
- **Dense Layer:** Classification layer with 512 units and 'relu' activation.
- **Dropout:** Regularization technique (rate = 0.5) to prevent overfitting.
- **LSTM Layer:** Adds capability to understand context within image data (128 units).
- **Output Layer:** Dense layer with 'softmax' activation for multi-class tumor prediction.

### Data 

- **Dataset:** Kaggle Brain Tumor MRI Dataset

- **Data Augmentation:**

  - `train_datagen`: ImageDataGenerator is used for data augmentation on the training set. This includes:
    - Rotation
    - Brightness adjustment
    - Shifting
    - Shearing
    - Horizontal flipping
  - `test_datagen`: No augmentation is applied to the test set, only rescaling.

- **Image Rescaling:**

    All images are rescaled by dividing pixel values by 255 (normalization to [0, 1] range).

- **Directory Structure:**

  Data is organized with each class in its own subdirectory.
    - `train_dir`: Path to the training images directory.
    - `test_dir`: Path to the testing images directory.

- **Generator Application:**

    `flow_from_directory`: This method applies the ImageDataGenerator, generating batches of augmented images and labels.

- **Class Indices:**

  - `class_indices_train`: Dictionary mapping training set class names to indices.
  - `class_indices_train_list`: is a list of class names for the training set. This provides a convenient way to access the class names in a list format.

- **Shuffling:**

  - Training data is shuffled (default in flow_from_directory).
  - Testing data maintains order (shuffle=False).

### Usage

1. **MRI Input:** Provide an MRI scan as input.
2. **Tumor Classification:** The model predicts the tumor class.
3. **Text Generation:** GEMMA creates a patient-friendly explanation of the results.

### Patient Impact

- **Clarity:** Patients receive accessible explanations of complex medical scans.
- **Understanding:** Promotes better understanding of their condition.
- **Medical Collaboration:** Fosters open communication with healthcare providers.

### Installation

**Prerequisites:**
- Python [version]
- TensorFlow/Keras
- GEMMA
- Other dependencies
