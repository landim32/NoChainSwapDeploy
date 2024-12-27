#FROM node:18
FROM nginx:alpine 

WORKDIR /var/www

COPY nochainswap /var/www/nochainswap
COPY big-whale /var/www/big-whale

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]