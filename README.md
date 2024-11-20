# Yolov8 Multitask Seg Det Internship 2024

## Description
This project focuses on optimizing safety and operations in the `railway` environment by developing a `multi-task` model.</br>
The model leverages the `YOLOv8` architecture, combining object detection and semantic segmentation to identify potential obstacles, track tracks, and analyze track-specific data.</br>
This project addresses unique challenges in the rail sector by adapting solutions from autonomous vehicles.</br>
The model is trained and evaluated to ensure high accuracy and reliability.

## Visuals
![results](images/results.png)

## ✨ Key Features
  * **Multitask Learning**: Integrated detection and segmentation tasks in a single model.
  * **Environment-Specific**: Designed specifically for railway scenarios.
  * **YOLOv8 Framework**: Forr real-time performance.

## 📂 Project Structure Overview
The Yolov8 model was finetuned on the [RailSem19](https://www.wilddash.cc/railsem19) dataset. All the code of the project can be found in the `Notebooks`. Here's an overview of the project

#### **1. Exploratory Data Analysis (EDA)**  
- **Dataset Familiarization**: understand its structure and annotations for both object detection and semantic segmentation.  
- **Class Selection**: Focused on specific classes relevant to project objectives:  
  - **Detection**:  
    - **Track-signal**: Railway traffic light signals.  
    - **Track-sign**: Signs along railways.  
    - **Vehicle**: Includes cars, trucks, and trains.  
    - **Person**: Critical for safety in railway environments.  
  - **Segmentation**:  
    - **Track**: Railway tracks for monitoring and maintenance.  
    - **Rail**: Metal components of the tracks.  
    - **Pole**: Structures supporting electrical systems (e.g., catenaries).  

#### **2. Training Process**  
- **Model Architecture**:  
  - Based on YOLOv8, chosen for its high real-time performance and precision.  
  - Includes a shared pre-trained **backbone** for both detection and segmentation tasks, adapted from a multitask model for autonomous vehicles.  
  - Features **four necks**: one for detection and three for segmentation **(tracks, rails, and poles)**.  

This is the model architecture:</br>
![results](images/model.png)

- **Weight Transfer**:  
  - The weights of the model are transferred from a backbone and segmentation weights of an autonomous vehicle multitask model, here's an overview of the transfer:  
    - **Lane segmentation** -> **Rail segmentation**.  
    - **Drivable areas** -> **Track segmentation**.  
    - **Pole class** was trained from scratch due to lack of transferability.  
    - **Detection Head** was trained from scratch also.



#### **3. Prediction**  
- Performed predictions on:  
  - **In-dataset images**: From RailSem19 dataset.  
  - **Out-of-domain videos**: Real-world railway scenarios to evaluate generalization.  

#### **4. Evaluation and Metrics**  

To evaluate the performance of the multitask model, we employed standard metrics for both detection and segmentation:  

- **Detection Metrics**: mAP@50, mAP@50-95, Precision, and Recall.  
- **Segmentation Metrics**: Pixel Accuracy, Mean Intersection over Union (mIoU), IoU, and Line Accuracy.  

These metrics provide a comprehensive evaluation of the model's ability to accurately detect and segment key features in the railway environment.</br>
Detailed calculations and results will be discussed in the following sections.  




