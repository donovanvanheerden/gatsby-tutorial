#build
FROM node:alpine as build

COPY package.json /src/

WORKDIR /src
RUN npm install

RUN npm install -g gatsby-cli

COPY . .
RUN npm run build

# production
FROM nginx:alpine

COPY --from=build /src/public /usr/share/nginx/html/

CMD ["nginx", "-g", "daemon off;"]