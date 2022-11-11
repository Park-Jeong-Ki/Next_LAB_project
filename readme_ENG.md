# Vehicle recognition & vehicle type classification using deep learning


colab example

[https://colab.research.google.com/drive/1-vBkeeQ0HrgCV95RHHlw405rXpWZRS31?usp=sharing]

---

## Project outline
| In collaboration with NextLab, we created a model that recognizes vehicles from CCTV images and categorizes vehicles!

Using YOLOV4, an object detection technology, 
we created a model that recognizes and crops vehicles from CCTV images, and classifies cropped vehicle images by using the EfficientNet model,which has the best performance among CNN models. 
I tried to verify that the CNN model can classify the brand, model, and year of the vehicle, and what part it looks at to classify it.

## Project Goals

| Recognizing and Cropping only car images from images with YOLO V4

| Classification of 322 car models using the EfficientNetV2 model

| Hypothesis validation with HeatMap

## conclusion

| We created a car model classification model with 89.6% validation data accuracy and 75% test data accuracy!

| With HeatMap, CNN also tested the hypothesis that it classifies car types by looking at the front of the car just like humans!

The model was trained with the vehicle model/year/number plate recognition image data provided by AI HUB. 
In the case of insufficient data, the number of data was unified through image augmentation. 
We improved the model performance with an augmentation technique tailored to fine-grained classification. 
With Dropout and Freeze, we were able to prevent overfitting the model and improve performance. 
After completing the model, the hypothesis of 'classifying vehicle types by looking at the vehicle's grille, headlights, and front part' was verified with the implementation of HeatMap. 
In the future, it is expected to be used in car parking lots and tunnel emissions prediction business models.
---

## Train/Validation Data
Use of "Vehicle for vehicle model/year/number plate recognition" shared on AI HUB: https://aihub.or.kr/aidata/27727
- Major categories: "Sedan", "SUB", "Hatchback", "Supply"
- Sub-category: 322 classes


## Test Data
Utilization of image data provided by NextLab company: https://www.nextlab.ai/
- About 80 kinds of tea image data


## Image data augmentation
Use of Augmentation Techniques Appropriate for Fine-grained Classification Problems
- CLAHE
- Contrast Normalization
- Sharpen
- Convolve

![image](https://user-images.githubusercontent.com/71398226/133566065-3ad87517-a771-4f19-a588-d3881cf3065e.png)


## Model Summary
![image](https://user-images.githubusercontent.com/71398226/133566602-30f73963-9303-435c-a3b5-7cb3776e83ee.png)

## Best Model Parameter
- Data augmented by 300 image data for all classes (322 types) (about 96600 sheets)
- EfficientV2 B0
- input size(224,224,3)
- input~30 layer freeze (learning regulation)
- use imagenet pretrained weights

## Best Model Result
![image](https://user-images.githubusercontent.com/71398226/133566684-8867e143-ca13-449b-af1a-460e3719e26c.png)

## HeatMap Result
![image](https://user-images.githubusercontent.com/71398226/133566790-3f96b1ef-d643-4633-9097-73645b56272e.png)

## Test Data Result
![image](https://user-images.githubusercontent.com/71398226/133567031-b4d92414-6fb1-4383-96b5-b2ab655d6d96.png)



