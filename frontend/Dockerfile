# stage 1: build React app
FROM node:18 AS builder

WORKDIR /app

COPY package.json ./
COPY public ./public
COPY src ./src

RUN npm install && npm run build

# ------------------------------------------------

# stage 2: serve with Nginx
FROM nginx:alpine

#COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=builder /app/build /usr/share/nginx/html


COPY default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

