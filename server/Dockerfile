from node:lts-alpine

workdir /app

copy package.json .

run npm install

copy . .

cmd ["npm", "run", "start"]
