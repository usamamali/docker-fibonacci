# base image
FROM node:alpine

WORKDIR /usr/app

# install dependencies

# make package.json in separate step to avoid installing npm dependencies every time we change in the code only
COPY package.json .
RUN npm install

COPY . .

# default command to run every time container started
CMD ["npm", "run", "start"]