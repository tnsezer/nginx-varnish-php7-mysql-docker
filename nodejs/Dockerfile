FROM node:latest

RUN mkdir /src

RUN npm install nodemon -g

WORKDIR /src


ADD . /src/

RUN npm install
RUN npm install -g

EXPOSE 3000
EXPOSE 3001

CMD npm start
