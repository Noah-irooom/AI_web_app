# AI_web_app

모바일앱 및 웹에서의 Tensorflow.js 구현

## 0.docker 설치 및 실행

0.1. 도커시작하기
- docker 설치후 cmd 열어서 root디렉토리로 이동
- $ docker ps -a  : 구성된 이미지 확인하기
- $ docker run -it -p 8080:8080 --name ubuntu1 ubuntu
  - 웹 전용 포트인 8080 또는 80으로 띄워야함.
- \# exit :  이미지 나가기

0.2. 도커 재시작하기
- $ docker start ubuntu1
- $ docker attach ubuntu1 또는 $ docker exec -it ubuntu1 bash

0.3. 도커에 기타 패키지 설치
- \# apt update : 먼저 업데이트해줘야 다음이 실행됨
- \# apt install nano : 편집기 설치
- \# apt install apache2 : 실습할 아파치 설치
- \# service apache2 start  : 아파치 시작하기

0.4 그외 도커 사용법
- cat /etc/issue  :  ubuntu 버전 확인
  - 20.04.2 LTS면 톰캣 보다는 아파치로 실습하는게 나을 듯. 
- $ docker rm -f ubuntu2 :  이미지 없애기
- 도커 완전 삭제 후 재설치
  - 프로그램 추가/제거에서 Docker Desktop installer제거
  - Program Files/Docker 폴더 삭제후 재설치
  - /User/user/AppData/Roaming/Docker 폴더 제거
    - Docker failed to initialize 해결법 아래 참고
    - https://stackoverflow.com/questions/68096476/docker-failed-to-initialize-on-windows 참고


## 1. CNN mnist 손글씨 숫자인식 예제
- Tensorflow 공식홈페이지 자바스크리트용 https://www.tensorflow.org/js/?hl=ko 참조
  
1.1. 
  
  
