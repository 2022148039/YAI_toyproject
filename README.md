YAI Toyproject : EfficientNet을 이용해서 리버스 강아지 번역기 만들기

### EfficientNet

- 강아지의 얼굴 사진들로 학습시켜 반려견이 바라보는 시선을 모델로 구현하고자함
- 기존 EfficientNet에서 Compound Scaling, Fused MBConv, ProgressiveLearning을 통해 학습 속도와 모델 크기, 메모리 효율을 개선한 EfficientNet V2 사용

### Dog Emotion Prediction Dataset

- 각 클래스당 1865개의 이미지로 이루어진 강아진 사진
- 5개의 class(happy, angry, alert, relax, frown)로 분류
- class당 8:2로 train과 validation set 구성

 학습 

- Google Colab, TPU v2 사용
- Output class: 1000개 (기존 EfficientNet) -> 5개
- Optimizer: RMS Prop, Scheduler: Cosine Annealing LR
  
  결과

- train accuracy: 86.79, validation accuracy: 72.91

한계점

- 인간이 임의로 분류한 강아지 표정 데이터셋
- 데이터셋에 얼굴만 나온 사진도 있고, 몸까지 다 나온 사진도 있음 -> 일관성 X
- ****부정적인 감정(angry, alert, frown) 사이의 뚜렷한 차이를 인식 못함
