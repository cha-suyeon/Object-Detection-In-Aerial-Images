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
- RetinaNet
    - FeedForward: RetinaNet
    - Backbone Network: FPN
    - Loss function: Focal Loss
- Detectron2 Framework

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
|![image](https://user-images.githubusercontent.com/84028683/146949450-631762f3-5fec-476e-9b47-e403348369cb.png)|![image](https://user-images.githubusercontent.com/84028683/146949430-c0236586-bd6a-4dec-a59d-350a086a43c0.png)|![image](https://user-images.githubusercontent.com/84028683/146949467-8503051e-da02-433f-bdc5-db2e00907f13.png)|![image](https://user-images.githubusercontent.com/84028683/146949490-0bddd97b-57fa-4c73-922b-da87d30464ed.png)
|--|--|--|--|
|차수연|김하늘|유상민|황동호|
