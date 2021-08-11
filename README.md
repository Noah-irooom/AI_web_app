# AI_web_app

모바일앱 및 웹에서의 Tensorflow.js 구현

## 0.docker 설치 및 실행

0.1. 도커시작하기
- docker 설치후 cmd 열어서 root디렉토리로 이동
- $ docker ps -a  : 구성된 이미지 확인하기
- $ docker run -it -p 8080:8080 --name ubuntu1 ubuntu
  - 웹 전용 포트인 8080 또는 80으로 띄워야함.
- ctrl + Q 또는 ctrl + P :  이미지 나가기

0.2. 도커 재시작하기
- $ docker start ubuntu1
- $ docker attach ubuntu1 또는 $ docker exec -it ubuntu1 bash

0.3. 도커에 기타 패키지 설치
- \# apt update : 먼저 업데이트해줘야 다음이 실행됨
- \# apt install nano : 편집기 설치
- \# apt install apache2 : 실습할 아파치 설치
- \# service apache2 start  : 아파치 시작하기

## 1.Tensorflow 공식홈페이지 자바스크리트용 https://www.tensorflow.org/js/?hl=ko 참조
  
1-1) CNN mnist 손글씨 숫자인식 예제
- 먼저

1.1.2. 
  
  
