# AI_web_app

모바일앱 및 웹에서의 Tensorflow.js 구현

## 0.docker 설치 및 실행

0.1. 도커시작하기
- docker 설치후 cmd 열어서 root디렉토리로 이동
- $ docker ps -a  : 구성된 이미지 확인하기
- $ docker run -it -p 80:80 -p 8080:8080 --name ubuntu1 ubuntu
  - 아파치는 포트 80으로 띄워야함.
- \# exit :  이미지 나가기

0.2. 도커 재시작하기
- $ docker start ubuntu1
- $ docker attach ubuntu1 또는 $ docker exec -it ubuntu1 bash

0.3. 도커에 기타 패키지 설치
- \# apt update : 먼저 업데이트해줘야 다음이 실행됨
- \# apt install nano : 편집기 설치
- \# apt install apache2 : 실습할 아파치 설치
- \# service apache2 start  : 아파치 서버 시작하기
- \# service apache2 stop : 아파치 서버 정지시키기

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
- 도커에서 로컬, 로컬에서 도커로 파일 이동 시키기
  - 도커 환경에 파일을 로컬로 가져오는 방법
    - docker cp CONTAINER-NAME:FILEPATH LOCALFILEPATH
    - 예) docker cp C:\Users\user\Desktop\Pytho_to_JS\model.json ubuntu3:/sample/
  - 로컬 환경에 도커 환경으로 파일 내보내는 방법
    - docker cp LOCALFILEPATH CONTAINER-NAME:FILEPATH


## 1. CNN mnist 손글씨 숫자인식 예제
- Tensorflow 공식홈페이지 자바스크리트용 https://www.tensorflow.org/js/?hl=ko 참조
  
1.1. docker 이미지 시작 후 해당 디렉토리로 이동
- $ docker start ubuntu1
- $ docker exec -it ubuntu1 bash
- \# cd /var/www/html

1.2. sample.html 생성후 코드 복붙
- https://codelabs.developers.google.com/codelabs/tfjs-training-classfication/index.html?hl=ko#1 참고
- 해당 페이지에 index.html 코드 내용을 우리 sample.html에 복사하여 붙여넣기
  - \# nano sample.html

1.3. data.js 생성 후 코드 복붙
- https://codelabs.developers.google.com/codelabs/tfjs-training-classfication/index.html?hl=ko#1 
- 위 링크에서 data.js 링크를 타고 들어가 코드 복사하여 붙여넣기
  - \# nano data.js 

1.4. script.js 생성 후 코드 복붙
- https://codelabs.developers.google.com/codelabs/tfjs-training-classfication/index.html?hl=ko#2 참고
- 해당 페이지의 script.js 코드를 복사하여 붙여넣기
  - \# nano script.js
- 그 후 service apache2 start하여 http://127.0.0.1/sample.html 접속하여 확인

1.5. script.js에 모델 아키텍쳐 코드 추가
- https://codelabs.developers.google.com/codelabs/tfjs-training-classfication/index.html?hl=ko#4 참고

1.6. script.js에 학습 함수 생성 코드 추가 및 실행
- https://codelabs.developers.google.com/codelabs/tfjs-training-classfication/index.html?hl=ko#5
- http://127.0.0.1/sample.html 페이지 새로고침 하면 학습이 진행됨.

1.7. script.js에 모델 평가 함수 생성 코드 추가 및 실행
- https://codelabs.developers.google.com/codelabs/tfjs-training-classfication/index.html?hl=ko#6
- http://127.0.0.1/sample.html 페이지 새로고침 하면 학습후 평가 진행
  
