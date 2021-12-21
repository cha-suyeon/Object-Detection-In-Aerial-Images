# Object-Dectection-In-Aerial-Images

## 🏁 Task
---
`Object Dectection In Aerial Images`
1. 인공위성 영상에서 목표 객체 검출 모델 구현
2. Scene 단위 영상(10,000x10,000)에서 객체 탐지
3. EDA를 통한 데이터 분석 후 검출 모델 성능 향상

</br>
</br>

## 🧠 Architecture
![image](https://user-images.githubusercontent.com/84028683/146949696-392656e1-ca4f-404b-bfd9-8f57e8655d13.png)
- RetinaNet
    - FeedForward: RetinaNet
    - Backbone Network: FPN
    - Loss function: Focal Loss

![image](https://user-images.githubusercontent.com/84028683/146949733-29ff2d1f-864c-4c21-b72a-f19273b27a89.png)
- Detectron2 Framework
    - COCO Detection

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

|||
|--|--|
|Detect Example 1 |Detect Example 2|

</br>
</br>

## 👩‍🔬 Team
---
- 차수연
- 김하늘
- 유상민
- 황동호
