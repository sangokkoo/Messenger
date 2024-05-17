# First stage: build the application
FROM node:16-slim as builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . ./
 
# Build the application for production
RUN npm run build

# nginx 서버를 사용할 경우
# FROM nginx:latest

# COPY --from=builder /app/build /usr/share/nginx/html

# RUN rm /etc/nginx/conf.d/default.conf

# COPY nginx/nginx.conf /etc/nginx/conf.d

# EXPOSE 80

# CMD ["nginx", "-g", "daemon off;"] 

# Second stage: use Node server for development
# node 서버를 사용할 경우
FROM node:16-slim

WORKDIR /app

COPY --from=builder /app /app

RUN npm install -g serve

EXPOSE 3000

CMD ["npm", "start"]
