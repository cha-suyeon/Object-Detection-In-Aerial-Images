# Object-Dectection-In-Aerial-Images

## 🏁 Task
`Object Dectection In Aerial Images`
1. 인공위성 영상에서 목표 객체 검출 모델 구현
2. Scene 단위 영상(10,000x10,000)에서 객체 탐지
3. EDA를 통한 데이터 분석 후 검출 모델 성능 향상

</br>
</br>

## 👩‍🔬 Contributor

|Name|Task|
|차수연|EDA, 데이터 포맷 변환, 모델 학습 및 분석, 최종 발표 및 PPT|
|김하늘|프로젝트 진행 방향 및 라이브러리 구현, 모델 학습 및 분석|
|유상민|프로젝트 서버, 모델 환경 구현, 모델 학습 및 분석|
|황동호|전반적 이슈에 대한 문제 해결 방법 서치, 모델 학습 및 분석, Large Image|

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

## 👩‍💻문제점 및 해결 방법

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

#### Dataset
![image](https://user-images.githubusercontent.com/84028683/146953535-5a7f4d12-c38a-4d54-95df-7f9ff2d1db7e.png)

</br>

#### Large Image

![image](https://user-images.githubusercontent.com/84028683/146953791-d115bf61-73af-491f-a5f5-e578186aa251.png)

</br>
</br>

## 📜 Paper Review

- 📃[YOLO: You Only Look Once - YOLO v1](https://velog.io/@cha-suyeon/%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-You-Only-Look-Once-YOLO-v1-v2-v3)
- 📃[YOLT: You Only Look Twice](https://velog.io/@cha-suyeon/%EC%A0%95%EB%A6%AC-You-Only-Look-Twice-Part-I)
- 📃[RetinaNet](https://velog.io/@cha-suyeon/Focal-Loss-for-Dense-Object-Detection)



