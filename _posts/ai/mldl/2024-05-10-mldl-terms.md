---
layout: post
bigtitle: "[Concept] - ML/DL Terms"
subtitle: "Terms Arrangement"
categories:
    - AI
    - ai-etc
# tags:
#   - python
#   - programming language
#   - basic
comments: true
# related_posts:
#    -
#    - 
published: true
---

## ML/DL 용어정리

---

*이미지를 기준으로 설명*

현실의 이미지를 컴퓨터로 옮길 때 컴퓨터는 이미지를 데이터로 전환 후 저장한다.

각 픽셀마다 수치 값을 가지고 있다.
픽셀마다 8bit를 기준으로 하면 0~255의 범위의 값을 가지고 있다.
$$
2^8 = 256
$$

1채널의 경우는 Grayscale로 흑백이미지라고 부른다.
1채널의 경우는 1개의 픽셀당 0~255 중 1개의 값을 가진다.

3채널(RGB..)는 우리가 흔히 접하는 경우고, 3개의 채널을 가지고 있어(R,G,B)를 각각의 3개의 값에 0~255의 중 1개의 값을 가져 (0,222,224) 같은 방식으로 값을 가지고 있다고 생각하시면 됩니다.

정리하면,
1채널 : 픽셀 1개당 0~255중 1개의 값
3채널 : 픽셀 1개당 0~255중 3개의 값 ex.(0,224,221)


- CNN : Convolutional Neural Networks, 합성곱 신경망, 주로 Computer Vision(CV)분야에서 쓰임, 사람의 뇌와 눈을 통한 시각적인 결과를 인공신경망을 통해 나타냄

- Convolutional : 합성곱
![Convolutional](/assets/img/AI/ai-etc/Convolution.gif)
필터가 이미지 위를 돌아다니면서 해당 픽셀값과 필터의 값을 곱해가면서 결과값(특징)을 추출함

- Channel : 채널
![Channel](/assets/img/AI/ai-etc/channel.jpg)
이미지에서 이미지 크기의 한 색상을 나타내는 값들의 집합
CNN에서 1개의 커널(필터)에 의해서 1개의 채널이 만들어짐
이미지에서 채널 : 위에 의미와 동일
CNN에서 채널 : 커널의 개수와 동일


- Filter : 필터
![Filter](/assets/img/AI/ai-etc/filter3.jpg)
커널이 weighted sum하는 영역의 크기
4x4x3이미지를 sliding windows를 하면서 커널이 돌아다니면 4x4이미지의 하나의 채널당 커널이 돌아다니게 되고 모든 채널의 값을 더할 시 4x4x3이 필터에 해당
필터의 크기 = weight의 개수

- Kernel : 커널

이미지 위에서 돌아다니는 하나의 값의 집합
sliding windows하는 영역에서의 크기
이미지의 특징을 찾아내기 위한 공용 파라미터
크기가 크면 클수록 더 많은 Feature 정보를 가져올 수 있음
지정된 간격을 이동하면서 채널별로 합성곱을 구해 하나의 Feature map을 구성

보통 CNN에서, 필터와 커널은 혼용되어서 사용함
![Filter/Kernel/Channel](/assets/img/AI/ai-etc/filter_kernel.png)


- Stride : 스트라이드
커널이 이미지 위를 지나다닐 때의 간격

- Padding : 패딩
![Padding](/assets/img/AI/ai-etc/padding.png)
입력 데이터의 외곽에 지정된 픽셀만큼 특정 값으로 채워 넣어 출력 데이터가 줄어드는 것을 방지
사이즈 조절 기능 + 이미지의 외곽이라는 것을 신경망에게 인식

- Pooling : 풀링
![Pooling](/assets/img/AI/ai-etc/pooling.png)
출력 데이터의 크기를 줄이거나 특정 데이터 강조
방식 : Max Pooling, Average Pooling
    - Max Pooling : 영역 안에서 최대 값을 추출
    - Average Pooling : 영역 안에서 평균 값을 추출

학습 대상 파라미터 없음, 채널 수 변경 없음, 행렬 크기 감소