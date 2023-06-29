# YOLOv8_Object_Detection
블로그로 보기 : https://lim123.tistory.com/133
기간 : 2023.6.12 ~2023.6.19 (7일)

프로젝트 착수(Initiation) : 

YOLOv8을 공부해보기 위해 프로젝트를 2단계로 구상했습니다.

첫 번째 단계에서는 ms-coco로 사전 학습(pre-training)된 욜로 모델 4가지를 불러와(n,s,l,x) 테스트 데이터셋에 사용하고 어떠한 이미지를 어떠한 모델이 정확히 분류하고 측정하는지 하는지 알기 위한 프로젝트입니다.
대체로 YOLOv8x가 좋게 나왔습니다.

두 번째 단계에서는 첫 번째 단계에서 대체로 좋은 성능을 보인 ms-coco로 pre-training된 YOLOv8x을 불러와 커스텀 데이터를 학습 시킵니다.

커스텀 데이터를 한가지만 사용해보기엔 부족한 것 같아 총 2가지 데이터셋을 학습시켰습니다 모두 로보플로우에서 제공하는 데이터를 사용했습니다.

1. AutomotiveFeatures Image (자동차기능 데이터셋)

2. Rock Paper Scissors SXSW (가위바위보 데이터셋)
   train set 11000(11k)
   Validation Set 604
   Testing Set 329



+자동차 기능 데이터셋은 class 총 2개 (자동차전체, 인테리어)
+가위바위보 데이터셋은 class 총 3개 (가위, 바위, 보)
 
# 첫 번째 단계
파일 : 
YOLOv8n~x성능.ipynb

내용 :
사전 MS-COCO 데이터셋으로 학습된 YOLOv8 의모델들 (YOLOv8n , YOLOv8s , YOLOv8l , YOLOv8x) 4가지 모델을 4개의 test image로 성능 test를 하였습니다.

결과 :
YOLOv8x 가 대체로 좋게 성능이 좋게 나왔습니다.

PPT:
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/18071254-fb00-45bf-ba7b-47ecbd6acaa1)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/8ad30a37-dd94-460b-81af-9685d073b930)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/1ef931f0-ab0f-404a-b717-73ab2e2d4c13)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/14823567-0544-4e6e-8c01-28be4563dff9)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/00549a16-d708-4768-807b-bc6e0e273f83)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/3cd529ef-aaba-44c6-9cdc-0477d1737096)


# 두 번째 단계

hyperparameter : 

Optimizer : Adam,
lr = 0.001667,
momentum = 0.9

결과: 

1.자동차전체 사진은 100% (1확률)로 정확히 탐지, 분류합니다 하지만 차량 내부 인테리어 분별은 정확하지 못합니다.
2.가위바위보를 50~60% 이지만 정확하게 탐지, 분류합니다.

PPT:
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/5e213616-19cb-4ef1-987c-10900bdaf2a3)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/581a2bef-c0ad-4e99-a75c-9daad3a14800)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/ae399256-24c8-4917-8825-4fd15233195c)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/84cb21e8-9ebb-46fe-9c93-410cb14b8ff3)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/c854da48-891b-40d8-91a6-f4ffc99a4c3d)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/7caeb9cb-48ba-4f25-b842-b55ddc6c4133)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/169ada9c-4e48-44a6-a539-88b27803bb03)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/ad7fc383-7dee-4661-a2a2-ed64e84fed60)
![image](https://github.com/limseo12/YOLOv8_Object_Detection/assets/93918673/84086dbb-7d25-4ab5-9714-69c57180cca7)



+학습 시작시 경로에 value 가 맞지 않다고 error가 떠서 학습시작이 불가능 하였으나
데이터셋을 다운로드 받는 코드를 다시 실행하면 문제없이 돌아간다.
colab의 문제인지는 정확히 알지 못함.

#reference
공식문서 : https://docs.ultralytics.com/modes/export/
깃허브 (git hub) : [neowizard](https://github.com/neowizard2018)
데이터셋 (Public Dataset) : https://public.roboflow.com/object-detection (roboflow)
