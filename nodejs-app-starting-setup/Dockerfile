# this docker file is done smarter so it copies nodee files first then applies code 
# changes after in order to speed up image creation

FROM node

WORKDIR /app

COPY package.json /app

# copy the minimum for the heavy install that way the intensive steps are cached.
# now if we make changes to the source code the build wont take forever.

RUN npm install

COPY . /app

EXPOSE 899

CMD ["node", "server.js"]

