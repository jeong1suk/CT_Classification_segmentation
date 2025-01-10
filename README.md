# MEDICAL IMAGING
---
* 문제 정의
* 실습 데이터셋 소개
* 데이터로더 구축
* 아키텍쳐 모델링
* 손실함수 구현
* 학습
* 테스트
순서로 진행

torchvision 라이브러리에서 제공하는 모델을 가져와서 실습데이터셋에 fine-tuning하는 작업

## 1. Classification
---
**정상, 코로나, 폐렴을 자동으로 분류할 수 있을까?** </br>
직접 판단해야하는 번거로움도 있고 크게 구분되는 특징이 없으면 불확실한 답을 내릴 수 있다. </br>

### 프로젝트 개요
- **목적**: 흉부 X-ray 이미지를 통해 정상, 코로나19, 바이러스성 폐렴을 자동으로 분류
- **모델**: VGG19 기반의 전이학습 모델
- **데이터셋**: 흉부 X-ray 이미지 (정상/Covid-19/바이러스성 폐렴)

### 구현 내용
1. **데이터 전처리**
   - 이미지 리사이징 (224x224)
   - RGB 정규화
   - Data Augmentation

2. **모델 아키텍처**
   - Pre-trained VGG19 모델 사용
   - Custom Classifier 레이어 추가:
     - Adaptive Average Pooling
     - Fully Connected Layers (512→256→3)
     - Softmax 활성화 함수

3. **학습 설정**
   - Loss Function: CrossEntropyLoss
   - Optimizer: SGD (learning rate=0.001, momentum=0.9)
   - Device: GPU (CUDA) 지원

4. **평가 지표**
   - Training/Validation Loss
   - Accuracy

### 사용 방법
1. 데이터셋 준비
   - train/test 폴더에 각각 Normal/Covid/Viral Pneumonia 클래스별 이미지 구성
   
2. 모델 학습
   - 10 에폭 학습 수행
   - 최고 성능 모델 자동 저장

3. 테스트
   - 저장된 모델을 로드하여 테스트 이미지에 대한 예측 수행
   - 예측 결과 시각화 기능 제공
   
## 2. Segmentation
---
## 3. Transfer Learning
---