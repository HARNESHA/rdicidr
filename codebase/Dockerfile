FROM node:15 as builder

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . . 

RUN npm run build

RUN ls -alh

FROM nginx:alpine

WORKDIR /usr/share/nginx/html

COPY --from=builder /app/build .

RUN ls -alh

ENTRYPOINT ["nginx", "-g", "daemon off;"]