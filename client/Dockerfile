FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
# copy the nginx cofig file to nginx base image default config to overide it
COPY ./default.conf /etc/nginx/conf.d/default.conf
# copy the build client image to the nginx root file
COPY --from=builder /app/build /usr/share/nginx/html