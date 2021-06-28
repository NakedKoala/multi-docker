# builder phase
FROM node:alpine
WORKDIR /app
COPY --chown=node:node package.json .
RUN npm install 
COPY --chown=node:node . .
RUN npm run build 

# Copy over only  artifact from build phase and start nginx
# Dumping all the FS snapshot from prev phase
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html