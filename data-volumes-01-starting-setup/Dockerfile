FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

# VOLUME ["/app/node_modules"] 
# can also be added using command line : -v /app/node_modules

CMD ["npm", "start"]