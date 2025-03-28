# VGG-16을 이용한 야채 이미지 분류

## 서론
- 야채는 색깔, 모양, 질감 등 여러 요소가 비슷할 수 있기 때문에 세심한 관찰이 필요
- 본 실험에서는 CNN 기반 Model을 통해 야채 이미지를 분류하는 작업을 수행
- 15가지의 Class로 이루어진 야채를 분류하여, 99% 이상의 Accuracy를 달성하는 것을 목표로 설정하였다

## 데이터
- Kaggle에 업로드된 [야채 데이터](https://www.kaggle.com/datasets/misrakahmed/vegetable-image-dataset/data)를 사용
- Training data는 각 Class마다 1000장, Validation과 Test의 경우 Class마다 200장
- 모든 이미지는 224x224의 jpg파일로 잘 전처리되어 있다

## 모델과 실험
### 모델: VGG-16
- 이전 미니퀘스트에서, VGG-16이 단순한 데이터에를 더 잘 처리하는 것을 보았다
- 복잡한 데이터가 아니기 때문에, ResNet과 같이 복잡도가 높은 Model을 사용하는 것이 오히려 과잉

### 실험
- Batch size: 16
- Data Augmentation: 15도 회전 및 좌우 대칭
- Optimizer: Adam with lr = 0.0001
- LR scheduler: 3연속으로 개선 없을 시 lr을 절반으로 한다
- Early stopping: 5연속으로 개선 없을 시 중단

## 결과
- 11 Epochs만에 Accuracy 99.7%로 매우 높은 성능을 달성하였다
- Pre-training data였던 ImageNet과 이 야채 데이터가 많이 겹쳤다
- 데이터가 전부 고화질, 일정한 각도 등 전처리가 너무 잘 되어 있던 것도 원인
