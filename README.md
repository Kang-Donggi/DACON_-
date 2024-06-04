# DACON anomaly detection on transistor

### 개요:
- 반도체 소자 데이터에서 이상탐지

### 데이터:
- MVTec transistor 데이터<br/>

|split|Images|Label|
|---|---|---|
|Train|213|X|
|Test|100|X|
<br/>
normal<br/>

![TRAIN_000](https://github.com/KANG-dg/object_detection_for_recycle/assets/121837927/85876f60-642d-4be0-8156-96755d45ff0a) <br/>

anrmal<br/>

![TEST_015](https://github.com/KANG-dg/object_detection_for_recycle/assets/121837927/fcccf108-da26-4aaf-ac44-ec56c320d2d9)

### 사용기법 & 결과:
- 해당 task는 정상 데이터만 학습시킨 후 test에서 이상데이터를 검출하는 anomaly detection
- backbone으로 resnet18을 사용해 feature 추출
- feature추출과정에서 모델이 이미지의 배경이 아닌<br/>
  transistor부분에 집중해서 학습할 수 있도록 centercrop 사용
- imagenet으로 사전학습된 backbone 모델에 transistor 데이터를 fine_tuning

### 결과 & 회고
- 위 방법으로 binary F1 score 기준 baseline 0.44에서 0.88로 성능 향상
- 특히 center crop을 통해 노이즈를 제거하는 방법에 성능 향상에 큰 효과
