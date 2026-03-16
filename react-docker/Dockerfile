# set the base image to create the image the react app 

FROM node:20-alpine

# create a user with permissions to run the app 
# -S -> Create a system user 
# -G app -> Add the user to the app group
# this is done to avoid running the app as root 
# if the app is run as root, any vulnerability in the app can be exploited to gain access to the host system
# IT's a good practice to run the app as a non-root user

RUN addgroup app && adduser -S -G app app

# set the user to run the app 
USER app

# set the working directory for the app 
WORKDIR /app

COPY package*.json ./

USER root

RUN chown -R app:app .

USER app

# install the app dependencies 
RUN npm install

# copy the app files to the container 
COPY . .


EXPOSE 5173

CMD npm run dev