# Object-Detection-In-Aerial-Images

## 🏁 Task
`Object Detection In Aerial Images`
1. 인공위성 영상에서 목표 객체 검출 모델 구현
2. Scene 단위 영상(10,000x10,000)에서 객체 탐지
3. EDA를 통한 데이터 분석 후 검출 모델 성능 향상

</br>
</br>

## 👩‍🔬 Contributor

|Name|Task|
|--|--|
|차수연|EDA, 데이터 포맷 변환, 모델 학습 및 분석, 최종 발표 및 PPT|
|김하늘|프로젝트 진행 방향 및 라이브러리 구현, 모델 학습 및 분석|
|유상민|프로젝트 서버, 모델 환경 구현, 모델 학습 및 분석|
|황동호|전반적 이슈에 대한 문제 해결 방법 서치, 모델 학습 및 분석, Large Image|

</br>
</br>

## 🚀 DATASET

- Dataset Download: [AI hub](https://aihub.or.kr/aidata/7982)
- 데이터 구성
    - 영상: kml + png + tif
    - Annotation: json
    - Patch Size: 1,024x1,024
- Large Image
    - type: tif
    - Pixel Size: 12362 x 11344

</br>
</br>


## 🧠 Architecture
![image](https://user-images.githubusercontent.com/84028683/146949696-392656e1-ca4f-404b-bfd9-8f57e8655d13.png)
- **RetinaNet**
    - FeedForward: RetinaNet
    - Backbone Network: FPN
    - Loss function: Focal Loss

- [**Detectron2 Framework**](https://github.com/facebookresearch/detectron2)
    - Detectron2 is Facebook AI Research's next generation library that provides state-of-the-art detection and segmentation algorithms.
    - We used COCO Detection algorithms.

</br>
</br>

## 👩‍💻 문제점 및 해결 방법

1. 학습 속도 개선
    - 2-stage 기반의 Faster R-CNN에서 RetinaNet으로 backbone network 변경
2. Data Imbalance
    - Category 분류 학습
3. Class Imbalance
    - RetinaNet의 Focal loss로 loss 값 조정
        - Positive/Negative Sample에 다른 가중치 부여
        - Easy/Hard Sample에 다른 가중치 부여
4. Oriented Bounding Box 구현 → 실패
    
    ![image](https://user-images.githubusercontent.com/84028683/146950221-a245772b-5391-4cd0-9b7b-47b346f094b8.png)
    
    위성영상 특성상, 객체가 회전해 있다는 특징으로 OBB 구현을 시도하였으나 실패함
    
    **원인**
    
    - OBB가 구현되는 network를 이용하지 못하였음
        - RBox Faster R-CNN을 사용하였다가 RetinaNet으로 network 변경
    - Framework toolkit 이용 방법
        - 객체를 회전 시킬 수 있는 툴킷이 있는 프레임워크 사용 시도 한계
        - 해커톤 때 이용한 Detectron2에는 맞는 기능이 없었음

</br>
</br>

## ⛰ Project Result

|Training Step|AP|AP50|AP75|
|--|--|--|--|
|10,000|8.104|16.200|8.642|
|25,000|11.280|22.66|10.910|
|50,000|12.321|23.320|11.770|
|150,000|13.140|23.475|13.262|

</br>

### Dataset
![image](https://user-images.githubusercontent.com/84028683/146953535-5a7f4d12-c38a-4d54-95df-7f9ff2d1db7e.png)

</br>

### Large Image

![image](https://user-images.githubusercontent.com/84028683/146953791-d115bf61-73af-491f-a5f5-e578186aa251.png)

</br>
</br>

## 📜 Paper Review

- 📃[YOLO: You Only Look Once - YOLO v1](https://velog.io/@cha-suyeon/%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-You-Only-Look-Once-YOLO-v1-v2-v3)
- 📃[YOLT: You Only Look Twice](https://velog.io/@cha-suyeon/%EC%A0%95%EB%A6%AC-You-Only-Look-Twice-Part-I)
- 📃[RetinaNet](https://velog.io/@cha-suyeon/Focal-Loss-for-Dense-Object-Detection)



---
## Project Objectives

- To detect focal objects of interest in the satellite imagery
- To improve performance with architecture and framework
- Analysis on the result such as object size and type

## Members

| Name | Role | Task |
| --- | --- | --- |
| 차수연 | Team member | EDA, Transform the dataset’s format, Training model and Analysis on the result and PPT. Mange GCP. |
| 김하늘 | Team leader | Manage the projects objectives. Training model and Analysis on the result. |
| 유상민 | Team member | Team member. Training model and Analysis on the result. Server management. |
| 황동호 | Team member | Team member. Training large Image and Analysis on the result. Issue management. |

## **Dataset**

- Dataset Download: [AI hub](https://aihub.or.kr/aidata/7982)
- Data Info
    - Images: kml + png + tif
    - Annotation: json
    - Patch Size: 1,024x1,024
- Large Image
    - type: tif
    - Pixel Size: 12362 x 11344
    

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

### Problems and Solutions

*Challenging tasks in Aerial Images*

Object detection in aerial images is a challenging task due to the massive variations of scale, rotation, aspect ratio, and densely arranged targets.

More importantly, the lack of large-scale benchmarks has become a major obstacle to the development of object detection in aerial images.

The dataset contains 424,750 object instances of 21 categories of oriented-bounding-box annotations collected from 1,748 aerial images.

Based on this large-scale and well-annotated dataset from AI hub, we built baselines covering various state-of-the-art detection and segmentation algorithms with framework Detectron2, where the speed and accuracy performances of each model have been evaluated.

*Problems and Solutions*

1. Speed up model training
- Chose the RetinaNet to match the speed of previous one-stage detectors while surpassing the accuracy of all existing state-of-the-art two-stage detectors
1. Address Class Imbalance
    - RetinaNet proposes the *Focal Loss*
        - Reshaping the standard cross entropy loss so that it down-weights the loss assigned to well-classified examples.
        - Focusing Training on a sparse set of hard examples and preventing the vast number of easy negatives from overwhelming the detector during training.
2. Data Imbalance
    - Separate the largest class from the others.
    - Train, evaluate and test two datasets separately.
3. Oriented Bounding Box
    
    ![image](https://user-images.githubusercontent.com/84028683/156780045-dcb17ee4-f9ea-44cc-be82-658f28767520.png)
    
    The variations of the orientation of objects is caused by the bird's-eye view of aerial images. So we tried to draw rotated bounding box, but couldn’t succeed.
    
    *Cause of failure*
    
    - We transformed the Dota dataset format to Coco to use Detectron2 baselines. In this process, the produced annotations only included gemetric annotations and failed to produce angle annotations.
    - We focused on the speed and accuracy performances rather than predicting accurately the rotated bounding box. (Detectron2 provided various backbone networks, so we can customize datasets for our task.)

## **Results**

- Metrics: Average Precision
    - The COCO Object Detection challenge also includes mean average recall as a detection metric. So we used average precision as a principal metric to evaluate object detectors. There are AP, AP50, AP75, mAP, AP@[0.5:0.95].

### **Dataset**

![https://user-images.githubusercontent.com/84028683/146953535-5a7f4d12-c38a-4d54-95df-7f9ff2d1db7e.png](https://user-images.githubusercontent.com/84028683/146953535-5a7f4d12-c38a-4d54-95df-7f9ff2d1db7e.png)

### **Large Image**

![https://user-images.githubusercontent.com/84028683/146953791-d115bf61-73af-491f-a5f5-e578186aa251.png](https://user-images.githubusercontent.com/84028683/146953791-d115bf61-73af-491f-a5f5-e578186aa251.png)

| Training Step | AP | AP50 | AP75 |
| --- | --- | --- | --- |
| 10,000 | 8.104 | 16.200 | 8.642 |
| 25,000 | 11.280 | 22.66 | 10.910 |
| 50,000 | 12.321 | 23.320 | 11.770 |
| 150,000 | 13.140 | 24.475 | 13.262 |

## **Paper Review**

- 📃[YOLO: You Only Look Once - YOLO v1](https://velog.io/@cha-suyeon/%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-You-Only-Look-Once-YOLO-v1-v2-v3)
- 📃[YOLT: You Only Look Twice](https://velog.io/@cha-suyeon/%EC%A0%95%EB%A6%AC-You-Only-Look-Twice-Part-I)
- 📃[RetinaNet](https://velog.io/@cha-suyeon/Focal-Loss-for-Dense-Object-Detection)

## Link

[Project Github](https://github.com/cha-suyeon/Object-Dectection-In-Aerial-Images)

[Presentation PPT](https://github.com/cha-suyeon/Object-Detection-In-Aerial-Images/blob/main/%ED%95%B4%EC%BB%A4%ED%86%A4%20%EB%B0%9C%ED%91%9C%20ppt.pdf)
