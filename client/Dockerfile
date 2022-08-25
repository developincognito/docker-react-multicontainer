FROM node:18-alpine3.15 as builder
WORKDIR '/app'
COPY ./package.json .
RUN npm config set strict-ssl false
RUN npm install --silent
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
#Default command starts nginx
