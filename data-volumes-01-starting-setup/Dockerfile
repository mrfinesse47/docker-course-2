FROM node:14

ARG DEFAULT_PORT=80

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .
# even if you use bind mounts for source code, it is useful to copy source to 
# images for production purposes.

ENV PORT ${DEFAULT_PORT}

EXPOSE ${PORT}

# once declared we can use env variables.

# VOLUME ["/app/node_modules"] 
# can also be added using command line : -v /app/node_modules

CMD ["npm", "start"]