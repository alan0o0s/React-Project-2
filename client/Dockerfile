FROM node:18-alpine AS buider

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

COPY . .

CMD [ "npm" , "run" , "start" ]


FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=buider /app/build /usr/share/nginx/html
