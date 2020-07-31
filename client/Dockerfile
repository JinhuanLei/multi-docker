FROM node:alpine as builder

WORKDIR '/app'

# package.json into /app folder
COPY package*.json ./
RUN npm install

COPY . .
# build step
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
