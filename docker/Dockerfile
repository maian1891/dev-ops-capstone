# build stage
FROM node:13.8.0-alpine as build-stage
WORKDIR /reactApp
COPY reactApp .
RUN npm install
RUN npm run build

# production stage
FROM nginx:1.17-alpine as production-stage
COPY --from=build-stage /reactApp/dist /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]