FROM node:16.5.0-alpine3.12

WORKDIR /root

COPY package.json .
COPY index.js .

RUN npm install

EXPOSE 3000

CMD [ "npm", "start" ]

