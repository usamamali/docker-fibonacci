# production Dockerfile

# base image for building the app
FROM node:alpine as builder

WORKDIR /usr/app

# install dependencies

# make package.json in separate step to avoid installing npm dependencies every time we change in the code only
COPY package.json .
RUN npm install

COPY . .
# build the app for production
RUN npm run build

# base image for nginx server to serve the app
FROM nginx

# expose port for elastic beanstalk
EXPOSE 3000

# copy nginx configuration file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# copy the build directory from the builder image to nginx html folder for serving the app
COPY --from=builder /usr/app/build /usr/share/nginx/html