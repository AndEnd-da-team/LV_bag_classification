# LV_bag_classification
_deskresearch for modeling_

협업 툴
- 코드 공유 : 깃헙
- 소통 : 디스코드
  
# todo 

1주차 목표
> 수집 -> 프로토타입 모델
## week1
- asdas
- as

[x] 모델 사이트 탐색  
[x] 도메인 지식 학습  
[x] 크롤링 및 데이터 수집 (초기 모델 학습 가능하도록)
  - 제품당 1000장 (중복 제외)


> 22.04.04
- 모델 사이트 탐색 : 중고명품 사이트 탐색  
  - result : 이베이, 구글
- 크롤링 코드 작성 완료
  - 밤새 크롤링하기

> 22.04.05
- 데이터 크롤링
  - result : 약 10 만장 크롤링
- 베이스 모델 만들기
  - result : conv autoencoder base coder

> 22.04.06
- 데이터 크롤링 : 이미지 30장 이하 모델 선별 및 데이터 재수집
  - result : 약 12만장 크롤링
- 데이터 검수 : 관련 없는 이미지 제거
  - reusult : 전체 데이터의 25% 검수
- 베이스 모델 만들기
  - result : ViT(patch16_224) base code w. gpu (making for TPU)

> 22.04.07
- [x] 도커 구축
- [x] 데이터 라벨링
- [x] 모델 성능 올리기 (ViT, patch16_224)

- 2차 시도 결과 : **정확도 0.48** (1차시 0.08)
  - 제품 수 : 424개
  - 이미지 데이터 수 : 6만개
  - 중복된 이미지 데이터가 있다고 판단
      - 전처리가 완벽하지 않아서 train set ⊃ validation set

- labeling 시작

  1. Docker setting
      - Docker 가상환경 구축
          - WSL 설치
          - git clone
      - 전처리 할 이미지 데이터 업로드 및 yolo 1.1 기준 label 사용
  2. labeling
      - 한 명당 500장
      - labeling 기준 (소요시간 : 약 2시간)
    
  
- 3차 시도 (object detection)

  - labeling img data를 활용한 학습 시도
  - Yolo v3 모델을 사용
  - [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AndEnd-da-team/LV_bag_classification/blob/endand_pmg/object_dectection/train_yolov3_bag.ipynb)
    - 3가지 라벨 사용: BigBag, SmallBag, BackPack
> 22.04.08
- shadow branch 만들기
  - naming rule : endand_000(이니셜)
- 깃허브 팀 룰 결정
  - 데이터 전처리 팀 : 박동환, 박형준
  - 모델링 팀
    - classification : 신동원
    - Auto Encoder for latent code : 박민규


> 22.04.12
- sha256 해쉬 기반 중복이미지 제거 코드 만들기
- EfficientNet b0 모델 시험
  - [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AndEnd-da-team/LV_bag_classification/blob/endand_pmg/classification/EfficientNetb0/classification_efficientnet.ipynb)
  - 실행 시간 : 6h
  - accuracy : 51.49 %
- 데이터 수집
  - 모델명 앞에 'Louis vuitton' 추가하여 정확한 데이터 수집 목적
- 임도형강사님 세미나

> 22.04.13
- 남은 인원들 구글 코랩Pro+ 결제요청 및 완료
- 데이터 크롤링 완료
- 이미지 디텍션 스터디

> 22.04.14
- 정확한 분류를 위해 분류를 1가지로 통일
  - 분류를 3개('Bigbag','Smallbag','Backpack')에서 1개(Bag)로 조정하기로 계획
- 학습시키지 않은 모델을 통한 이미지 탐지 OPENCV2-YOLO
    - 샘플링테스트결과 : 7개 중 3개 정도로 탐지

> 22.04.15
- 대표님과의 회의
  - 미팅 - 화요일 금요일 10시 고정
- 전처리
    
> 22.04.18
- 전처리를 위한 모델 학습

> 22.04.19
- 전처리 모델 프로토타입 완료
- [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AndEnd-da-team/LV_bag_classification/blob/endand_pdh/YOLO-openCV2/YOLO-openCV2.ipynb
)
- 회의
  - 구글 드라이브 저장공간 요청

> 22.04.20
- 전처리를 위한 모델 학습
- 전처리 모델 성능 업그레이드를 위한 분류를 3개('Bigbag','Smallbag','Backpack')에서 1개(Bag)로 조정

> 22.04.21
- 이미지 디텍션 코드 작성
- [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AndEnd-da-team/LV_bag_classification/blob/endand_pdh/object_dectection/IMG_Data%20Preprocessing.ipynb
)


  - 기술멘토님 도움 받아 문제 해결 (패키지 버전문제)

> 22.04.22
- 이미지 디텍션 코드 작성
- 대표님과의 회의
- 탐지 이미지 샘플 시각화
- 가방 탐지 함수 생성
  -  이후 테스트 진행

> 22.04.23 ~ 22.04.24
- 데이터 클리닝
  - 전 : 약 13만 장
  - 후 : 약 8천 장

> 22.04.25 ~ 22.04.27
- 모델 실험 및 평가
  - 최종 모델 선택 : EfficientNetB0
