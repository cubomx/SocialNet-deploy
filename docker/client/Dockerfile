FROM node:16-alpine

RUN npm install --location=global @angular/cli

RUN apk update && apk add git

WORKDIR /app

CMD git clone https://github.com/cubomx/SocialNet-Front.git \ 
&& cd SocialNet-Front && npm install && npm start
