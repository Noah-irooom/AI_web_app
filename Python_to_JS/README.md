# Convert pretrained model with python to JS version

## Tensorflow.js in Node (node.js)
### 1. 코랩에서 파이썬 코드로 모델 학습 진행하기
- https://www.tensorflow.org/tutorials/quickstart/beginner?hl=ko 참고
- 해당 페이지의 코랩환경에 들어가서  mnist 데이터로 간단한 모델을 학습시킨다.
- 코랩 ipynb파일은 현 디렉토리에 업로드 되어있다. -> 
- Output으로 sample.h5 모델이 저장되는 이를 다운로드한다.

### 2. 코랩에서 파이썬 모델을 자바스크립트 모델로 변환하기
- !mkdir sample : sample 폴더 생성하기
- !pip3 install tensorflowjs
- !tensorflowjs_converter --input_format keras  sample.h5  sample
  - sample.h5모델을 변환하여 sample 디렉토리에 저장하겠다.
  - 아웃풋으로는 group1-shard1of1.bin,  model.json 파일이 저장됨.
  - 즉 모델이 JSON형식으로 변환되어 저장됨.

### 3. Docker settings
- 3.1. 이제 도커를 실행한다. 단, 포트포워딩이 된 도커를 실행.
  - $ docker start ubuntu1
  - $ docker exec -it ubuntu1 bash
- 3.2. 기타 세팅 맞추기
  - \# apt update
  - \# apt install nodejs
  - \# apt install npm
  - \# npm install -g typescript
- 3.3. mkdir sample; cd sample  :  sample 디렉토리 생성후 들어가기
- 3.4. npm init -y
  - package.json 생성됨
- 3.5. npm install -g @tensorflow/tfjs  
  - node_modules 생성됨
  - 단, node.js를 실행할 땐, apache가 정지되어 있어야함. 포트가 겹칠 수 있기 때문. 물론 반대도 마찬가지.
    - service apache2 stop

### 4. Node.js에서 모델 학습 진행하기
- 위과정과는 별도로 잠깐 테스트용이다. node.js가 잘 동작하는지 확인 위해.
- https://www.tensorflow.org/js/guide/nodejs?hl=ko 참고
- 4.1. \# nano sample.js : 생성하여 위 링크 코드 작성
  - 단, 현재(2021.08.12)기준으로 공식 문서 코드가 오류가 뜸.
    - import * as tf from '@tensorflow/tfjs-node' 대신에  const tf = require('@tensorflow/tfjs') 사용
    - // callbacks: tf.node.tensorBoard('/tmp/fit_logs_1') : 텐서보드 콜백은 일단 주석처리하여 실행

- 4.2. \# node sample.js 로 실행하기.

### 5. 변환된 모델 로드하여 Node.js에서 inference 진행하기
- 자바스크립트로 변환된 모델 로드 하여 inference하기
  
