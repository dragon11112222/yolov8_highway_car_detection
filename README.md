# yolov8_highway_car_detection
ai hub 교통문제 해결을 위한 cctv 교통 영상(고속도로) 데이터 내 수도권 영동선 데이터 활용하여 car, bus, truck 탐지

1. [local] 데이터 압축 풀기 test
2. [local] 라벨 xml 2 txt test
3. [local] 바운딩 박스 그려보기 test
4. [gcp] 클라우드 인스턴스 준비
5. [gcp] 클라우드 스토리지 버킷에 데이터 압축파일 업로드
6. [gcp] 클라우드 스토리지 버킷과 주피터 폴더 연동(mount)
7. [gcp] 주피터 파일로 버킷에 압축풀기
8. [gcp] 라벨 xml 2 txt
9. [gcp] 학습에 활용할 일부 파일(CH01~04, .png & .txt)만 새로운 폴더에 재구성

10. [gcp] yolo 학습 기본 코드 돌려보기
Ultralytics YOLOv8.0.215 🚀 Python-3.10.13 torch-1.13.1+cu117 CUDA:0 (Tesla V100-SXM2-16GB, 16161MiB)
                                                              CUDA:1 (Tesla V100-SXM2-16GB, 16161MiB)
YOLOv8n summary (fused): 168 layers, 3006233 parameters, 0 gradients, 8.1 GFLOPs
val: Scanning /home/jupyter/highway/bbox_highway/test/labels.cache... 3333 images, 0 backgrounds, 0 corrupt: 100%|██████████| 3333/3333 [00:00<?, ?it/s]
                 Class     Images  Instances      Box(P          R      mAP50  mAP50-95): 100%|██████████| 27/27 [01:51<00:00,  4.14s/it]
                   all       3333      51017      0.672      0.602      0.653      0.457
                   car       3333      38759      0.812      0.817      0.869      0.631
                   bus       3333       1868      0.623      0.378      0.477      0.319
                 truck       3333      10390      0.582      0.611      0.614      0.421
Speed: 0.2ms preprocess, 0.7ms inference, 0.0ms loss, 0.9ms postprocess per image

11. [gcp] 데이터 분석(라벨 클래스 비율 등)으로 학습시킬 이미지 데이터 선별 ------> 여기까지 완료
12. [gcp] 버스 & 배경 이미지 데이터 증식 및 재구성
13. [gcp] yolo 재학습
14. [gcp] cycle gan 모델 등으로 학습용 이미지 데이터 증식

- local
  - conda 23.7.4
    - python 3.8.18
      - pandas 2.0.3
      - numpy 1.24.4
      - lxml 4.9.3
      - cv2 4.8.1
- google cloud platform
  - gpu : Tesla V100-SXM2-16GB 2개
  - cpu : 4개
  - ram : 15GB
  - python 3.10.13
    - numpy 1.23.5
    - lxml 4.9.3
    - distutils 3.10.13
    - torch 1.13.1+cu117
    - torchvision 0.14.1+cu117
    - ultralytics 8.0.215
    - IPython 8.17.2
