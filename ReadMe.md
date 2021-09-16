# 딥러닝을 활용한 차량 인식 & 차종 분류

## 프로젝트 개요
| NextLab 기업과 협업 하여 CCTV 영상에서 차량을 인식하고, 차종을 분류하는 모델을 만들었습니다!

Object Detection 기술인 YOLOV4를 활용해서 CCTV 영상에서 차량을 인식하여 Cropping하고, CNN 모델 중에 최근 성능이 가장 좋았던 EfficientNet 모델을 활용해서 Cropping된 차량 이미지를 어떠한 차종인지 분류해 내는 모델을 만들었습니다. 과연 CNN 모델이 차량의 브랜드, 모델, 연식 까지 분류해 낼 수 있는지, 어떤 부분을 보고 분류를 하는지 검증해 보았습니다

## 프로젝트 목표

| YOLO V4로 이미지에서 차 이미지만 인식 및 Cropping

| EfficientNetV2 모델을 활용하여 322개의 차종을 분류 

| HeatMap으로 가설 검증

## 결론

| 검증 데이터 정확도 89.6%, 테스트 데이터 정확도 75%의 차종 분류 모델을 만들었어요! 

| HeatMap으로 CNN도 사람과 같이 차량의 앞부분을 보고 차종을 분류한다는 가설을 검증 했어요!

AI HUB 에서 제공하는 차종/연식/번호판 인식 영상 데이터를 가지고 모델을 학습 시켰습니다. 부족한 데이터는 이미지 증강을 통해서 데이터 개수를 통일 시켜주었어요. Fine-grained classification에 맞춘 증강 기법으로 모델 성능을 높였습니다. Dropout과 Freeze로 모델의 과적합을 막고 성능을 향상 시킬 수 있었습니다. 모델 완성 후 '차량의 그릴, 헤드라이트, 앞부분을 보고 차종을 분류한다'는 가설을 HeatMap 구현으로 검증 했습니다. 추후 자동차 주차장, 터널안 배기량 예측 사업 모델에 사용할 수 있을 것으로 예상됩니다.


---

## Train/Validatation Data
AI HUB에 공유된 "자동차 차종/연식/번호판 인식용 영상" 사용: https://aihub.or.kr/aidata/27727
- 대분류: "세단", "SUB", "해치백", "승합"
- 소분류: 322개의 클래스


## Test Data
NextLab 기업에서 주신 이미지 데이터 활용 : https://www.nextlab.ai/
- 약 80 종의 차 이미지 데이터 


## Image data Augmentation
Fine-grained Classification 문제에 알맞은 증강 기법 사용
- CLAHE
- Contrast Normalization
- Sharpen
- Convolve

![image](https://user-images.githubusercontent.com/71398226/133566065-3ad87517-a771-4f19-a588-d3881cf3065e.png)


## Best Model Parameter
- 모든 class(322종)에 대해 이미지 데이터 300개씩 증강한 데이터 (약 96600장)
- EfficientV2 B0 
- input size(224,224,3)
- input~30 layer freeze (학습규제)
- imagenet pretrained 가중치 사용

---
colab 예시

[https://colab.research.google.com/drive/1-vBkeeQ0HrgCV95RHHlw405rXpWZRS31?usp=sharing]
