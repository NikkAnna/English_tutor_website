FROM node:18 as build
WORKDIR app
COPY package.json /app/
RUN npm install
COPY . /app
RUN npm run build

FROM nginx
WORKDIR /usr/share/nginx/html
COPY --from=build /app/dist/ .
EXPOSE 3443
EXPOSE 80
EXPOSE 443
COPY deploy/nginx.conf /etc/nginx/nginx.conf
