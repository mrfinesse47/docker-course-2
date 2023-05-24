FROM node 
#interesting that a React app needs to use a node image. Could be a potential gotcha.
WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

CMD ["npm","start"]

EXPOSE 3000

