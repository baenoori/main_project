## 💪 나만의 AI 홈트레이너 
주제 : 사용자에게 적합한 맞춤형 운동 횟수 추천과 Machine Vision을 이용한 올바른 자세 피드백을 제공하는 대화형 AI 홈트레이너 구현

기간 : 2024.10.22 - 2025.01.08

인원 : 4명 (배누리, 박현아, 전사영, 김호정)

<br>

## 프로젝트 소개
### 나만의 AI 홈트레이너

![Image](https://github.com/user-attachments/assets/aa489cb5-01d3-4f24-bf5f-7c547c38ad76)

**1. 데이터**
- AIHUB에 있는 피트니스 데이터셋을 활용하려 했으나 YOLO와 mediapipe로 추출한 데이터와 오차가 있어 사용이 불가하다고 판단
- 유튜브에 있는 다양한 운동 영상을 활용해 직접 MediaPipe를 활용하여 x, y, z 데이터를 추출하여 csv로 만들어 사용
- 각 운동별(런지, 플랭크, 스쿼트, 푸시업, 크런치)로 필요한 관절 좌표만 사용하여 훈련 진행 

<br>

**2. 모델 구성**
- CatBoost, XGBoost, LightGBM, NGBoost로 정자세/오자세 이진 분류 모델 학습 및 Voting, Stacking, 전이 학습 진행 후 가장 좋은 모델 저장
- 성능 비교 (Acc)

![Image](https://github.com/user-attachments/assets/a4ca54e2-a47b-449d-b118-631f11f6ae8a)

<br>

**3. LangChain을 활용한 운동 횟수 및 세트 추천 및 피드백 제공**
- 사용자가 입력한 정보를 기반으로 OpenAI가 운동 횟수 및 세트 추천
- 사용자는 추천된 운동 횟수 및 세트 기반으로 운동을 진행
- 운동이 모두 끝난 후에는 저장된 피드백 데이터를 통해 전반적인 운동에 대한 피드백과 소모 칼로리 등 제공 및 운동에 대한 간단한 대화 가능

<br>

**4. YOLO와 MediaPipe를 활용한 자세 분류(정자세/오자세) 및 실시간 피드백 제공**
- 사용자가 운동을 시작하면 YOLO로 사람을 탐지하고 탐지된 프레임 내에서 MediaPipe로 좌표 추출
- 추출된 좌표를 이전에 학습한 모델을 사용하여 정자세/오자세 예측
- 정자세일 경우 횟수 Count 진행
- 오자세일 경우 피드백 출력

<br>

**5. streamlit을 활용한 웹 구현**
- 사용자 정보 입력, 운동 선택, 운동 안내, 운동 진행, 피드백 등 시각화 진행 


<br>

**6. IP Webcam 과 Android Studio를 활용한 웹뷰 앱 구현**
- 휴대폰 카메라 연결을 위해 IP Webcam 어플 사용
- streamlit으로 구현한 웹을 앱에서 볼 수 있도록 웹뷰 앱 구현

[시연 영상>]([[메인프로젝트]나만의 AI 홈트레이너/notebooks/[최종팀프로젝트]나만의 AI 홈트레이너_배누리_시연영상.mp4](https://github.com/baenoori/main_project/blob/master/%5B%EB%A9%94%EC%9D%B8%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%5D%EB%82%98%EB%A7%8C%EC%9D%98%20AI%20%ED%99%88%ED%8A%B8%EB%A0%88%EC%9D%B4%EB%84%88/notebooks/%5B%EC%B5%9C%EC%A2%85%ED%8C%80%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%5D%EB%82%98%EB%A7%8C%EC%9D%98%20AI%20%ED%99%88%ED%8A%B8%EB%A0%88%EC%9D%B4%EB%84%88_%EB%B0%B0%EB%88%84%EB%A6%AC_%EC%8B%9C%EC%97%B0%EC%98%81%EC%83%81.mp4))

