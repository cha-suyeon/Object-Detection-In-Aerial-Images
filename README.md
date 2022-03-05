# Object-Detection-In-Aerial-Images
### Project Objectives

- To detect focal objects of interest in the satellite imagery
- To improve performance with architecture and framework
- Analysis on the result such as object size and type

<br/>

### Members

| Name | Role | Task |
| --- | --- | --- |
| 차수연 | Team member | EDA, Transform the dataset’s format, Training model and Analysis on the result and PPT. Mange GCP. |
| 김하늘 | Team leader | Manage the projects objectives. Training model and Analysis on the result. |
| 유상민 | Team member | Team member. Training model and Analysis on the result. Server management. |
| 황동호 | Team member | Team member. Training large Image and Analysis on the result. Issue management. |

<br/>

### **Dataset**

- Dataset Download: [AI hub](https://aihub.or.kr/aidata/7982)
- Data Info
    - Images: png + tif
    - Annotation: json
    - Geographic context: Kml
    - Patch Size: 1,024x1,024
- Large Image
    - type: tif
    - Pixel Size: 12362 x 11344
    
<br/>

### Model Architecture
- **RetinaNet**
    
    ![image](https://user-images.githubusercontent.com/84028683/156780000-d8ba593d-ed32-473f-a806-0ce56d3afa4b.png)
    
    - Feed Forward Network: ResNet
    - Backbone Network: FPN (Feature Pyramid Networks)
    - Loss function: Focal Loss
- **[Detectron2 Framework](https://github.com/facebookresearch/detectron2)**
    - Detectron2 is Facebook AI Research's next generation library that provides state-of-the-art detection and segmentation algorithms.
    - We trained a dectection model from an existing model pre-trained on the COCO dataset, available in detectron2's model zoo.
    - We chose [R101](https://github.com/facebookresearch/detectron2/blob/main/configs/COCO-Detection/retinanet_R_101_FPN_3x.yaml) in RetinaNet baselines.

<br/>

### Problems and Solutions

*`Challenging tasks in Aerial Images`*

Object detection in aerial images is a challenging task due to the massive variations of scale, rotation, aspect ratio, and densely arranged targets.

More importantly, the lack of large-scale benchmarks has become a major obstacle to the development of object detection in aerial images.

The dataset contains 424,750 object instances of 21 categories of oriented-bounding-box annotations collected from 1,748 aerial images.

Based on this large-scale and well-annotated dataset from AI hub, we built baselines covering various state-of-the-art detection and segmentation algorithms with framework Detectron2, where the speed and accuracy performances of each model have been evaluated.

*`Problems and Solutions`*

1. Speed up model training
    - Chose the RetinaNet to match the speed of previous one-stage detectors while surpassing the accuracy of all existing state-of-the-art two-stage detectors
  
2. Address Class Imbalance
    - RetinaNet proposes the ***Focal Loss***
        - Reshaping the standard cross entropy loss so that it down-weights the loss assigned to well-classified examples.
        - Focusing Training on a sparse set of hard examples and preventing the vast number of easy negatives from overwhelming the detector during training.

3. Data Imbalance
    - Separate the largest class from the others.
    - Train, evaluate and test two datasets separately.

4. Oriented Bounding Box
    
    ![image](https://user-images.githubusercontent.com/84028683/156780045-dcb17ee4-f9ea-44cc-be82-658f28767520.png)
    
    The variations of the orientation of objects is caused by the bird's-eye view of aerial images. So we tried to draw rotated bounding box, but couldn’t succeed.
    
    *`Cause of failure`*
    
    - We transformed the Dota dataset format to Coco to use Detectron2 baselines. In this process, the produced annotations only included gemetric annotations and failed to produce angle annotations.
    - We focused on the speed and accuracy performances rather than predicting accurately the rotated bounding box. (Detectron2 provided various backbone networks, so we can customize datasets for our task.)

<br/>

### **Results**

- Metrics: Average Precision
    - The COCO Object Detection challenge also includes mean average recall as a detection metric. So we used average precision as a principal metric to evaluate object detectors. There are AP, AP50, AP75, mAP, AP@[0.5:0.95].

#### **Dataset**

![https://user-images.githubusercontent.com/84028683/146953535-5a7f4d12-c38a-4d54-95df-7f9ff2d1db7e.png](https://user-images.githubusercontent.com/84028683/146953535-5a7f4d12-c38a-4d54-95df-7f9ff2d1db7e.png)

#### **Large Image**

![https://user-images.githubusercontent.com/84028683/146953791-d115bf61-73af-491f-a5f5-e578186aa251.png](https://user-images.githubusercontent.com/84028683/146953791-d115bf61-73af-491f-a5f5-e578186aa251.png)

| Training Step | AP | AP50 | AP75 |
| --- | --- | --- | --- |
| 10,000 | 8.104 | 16.200 | 8.642 |
| 25,000 | 11.280 | 22.66 | 10.910 |
| 50,000 | 12.321 | 23.320 | 11.770 |
| 150,000 | 13.140 | 24.475 | 13.262 |

<br/>

### **Paper Review**

- 📃[YOLO: You Only Look Once - YOLO v1](https://velog.io/@cha-suyeon/%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-You-Only-Look-Once-YOLO-v1-v2-v3)
- 📃[YOLT: You Only Look Twice](https://velog.io/@cha-suyeon/%EC%A0%95%EB%A6%AC-You-Only-Look-Twice-Part-I)
- 📃[RetinaNet](https://velog.io/@cha-suyeon/Focal-Loss-for-Dense-Object-Detection)

<br/>

### Link

[Project Github](https://github.com/cha-suyeon/Object-Dectection-In-Aerial-Images)

[Presentation PPT](https://github.com/cha-suyeon/Object-Detection-In-Aerial-Images/blob/main/%ED%95%B4%EC%BB%A4%ED%86%A4%20%EB%B0%9C%ED%91%9C%20ppt.pdf)
