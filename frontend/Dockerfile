FROM node:lts-alpine as base-image
WORKDIR /frontend
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.21.4 as run-stage
COPY --from=base-image /frontend/build /usr/share/nginx/html
EXPOSE 80
CMD nginx -g daemon off;