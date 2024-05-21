# American Sign Language Detection using YOLOv7
```markdown

This project aims to detect American Sign Language (ASL) gestures using the YOLOv7 object detection model.

The application is built using Flask for the backend and integrates with YOLOv7 for real-time and image-based ASL detection.
```
## Table of Contents
- [Installation](#installation)
- [Dataset](#dataset)
- [Training](#training)
- [Running the Application](#running-the-application)
- [Results](#results)

## Installation

### Cloning the Repository
First, clone the YOLOv7 repository and install the required dependencies.

```bash
!git clone https://github.com/augmentedstartups/yolov7.git
%cd yolov7
!pip install -r requirements.txt
!pip install roboflow
```

## Dataset

### Downloading the Dataset
We will use Roboflow to download the ASL dataset.

```python
from roboflow import Roboflow
rf = Roboflow(api_key="BwXJGIF4PyPURTjVcg0y")
project = rf.workspace("yolo-bkh56").project("signlanguage-hcsec")
dataset = project.version(3).download("yolov7")
```

## Training

### Downloading Pre-trained Weights
Download the pre-trained YOLOv7 weights.

```bash
wget https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt
```

### Training the Model
Train the YOLOv7 model on the ASL dataset with 60 epochs.

<!-- ```bash
%cd yolov7
!python train.py --img 640 --batch 4 --cfg cfg/training/yolov7.yaml --epochs 60 --data signlanguage-3/data.yaml --weights 'yolov7.pt' --cache --device 0
``` -->

## Running the Application

### Flask Application
The Flask application (`app.py`) handles image uploads and real-time detection.

Run the Flask application to start the server.

```bash
python app.py
```

## Results

### Evaluation Metrics
The model's performance is evaluated using F1 score, precision, and confusion matrix.

### Testing the Model
Test the model on the ASL test images.

#### Confusion Matrix 
![image info](https://github.com/adityaazad79/Sign_Lang_Detection/blob/master/Images/Confusion_Matrix.png?raw=true)

#### F1 Curve
![image info](https://github.com/adityaazad79/Sign_Lang_Detection/blob/master/Images/F1_Curve.png?raw=true)

#### PR Curve
![image info](https://github.com/adityaazad79/Sign_Lang_Detection/blob/master/Images/PR_Curve.png?raw=true)



Citations:

[1] https://github.com/augmentedstartups/yolov7.git

[2] https://github.com/WongKinYiu/yolov7/releases/download/v0.1/yolov7.pt