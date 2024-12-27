# Stage 1: Build the React Application
#FROM node:18
FROM nginx:alpine 

WORKDIR /app

COPY . .

# Stage 2: Setup the Nginx Server to serve the React Application

COPY CodeDevClub /var/www/codedevclub
COPY BEHR /var/www/behr
COPY WB3 /var/www/wb3

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]