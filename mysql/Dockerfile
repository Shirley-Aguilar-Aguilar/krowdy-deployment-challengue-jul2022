FROM node:10-alpine
WORKDIR /var/www
COPY package.json .
RUN npm install
COPY . .
EXPOSE 8077
CMD ["node", "index.js"]