# node.js 이미지를 바탕으로 컨테이너를 실행한 후
# http://localhost:3333으로 접속했을 때 hello from server 메시지가 표시되게 만드세요
# 아래에 적은 코드들은 모두 다 컨테이너 안에서 작동할 애들임 
FROM node:16-alpine

# 앱 디렉터리 생성
# 얘는 내 컨테이너 안의 경로임 
WORKDIR /usr/src/app

# 앱 의존성 설치
# 가능한 경우(npm@5+) package.json과 package-lock.json을 모두 복사하기 위해
# 와일드카드를 사용
# 여기서 말하는 ./는 /usr/src/app를 말하는거임
COPY package*.json ./

RUN npm install
# 프로덕션을 위한 코드를 빌드하는 경우
# RUN npm ci --only=production

# 앱 소스 추가
# 처음 .은 현재경로 두번째 .은 /usr/src/app임 이 컨테이너 안에서 npm install까지 다된걸 저 경로로 넘기기
COPY . .

# 도커한테 이 컨테이너 안에서는 80포트를 쓰겠다고 알려주는 거랑 같음 
EXPOSE 3000

#CMD 위에 쓴 애들은 이미지를 만들기 위해서 작성한 것이고 
#CMD는 이 이미지로부터 컨테이너를 생성하여 실행할 때 수행하는 것 
CMD [ "node", "app.js" ]