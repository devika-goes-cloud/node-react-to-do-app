# Build Stage
FROM node:14-alpine as frontend-build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . . 

RUN npm run build  # creates /usr/src/app/build



# Run Stage 
FROM nginx:alpine

COPY --from=frontend-build  /app/build/ /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
