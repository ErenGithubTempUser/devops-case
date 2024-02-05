FROM node:16 as builder

WORKDIR /app

COPY package-lock.json package.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx:1.21-alpine

RUN rm -rf /usr/share/nginx/html/*

COPY --from=builder /app/build /usr/share/nginx/html

WORKDIR /usr/share/nginx/html

CMD ["nginx", "-g", "daemon off;"]
