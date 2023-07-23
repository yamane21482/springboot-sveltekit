FROM --platform=$BUILDPLATFORM node:18.3.0-alpine3.14

RUN mkdir /project
WORKDIR /project

COPY . .

RUN npm install -g npm
RUN npm install
EXPOSE 5173
CMD [ "npm", "run", "dev", "--host" ]
