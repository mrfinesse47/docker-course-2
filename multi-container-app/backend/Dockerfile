FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

# this prevents layer bottle necks as the npm install will not have to be re run on source changes.

EXPOSE 80

CMD ["node","app.js"]

