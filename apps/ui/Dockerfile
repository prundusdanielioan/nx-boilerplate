FROM nginx:1.21.1-alpine

WORKDIR /app

COPY ./apps/ui/nginx.conf /etc/nginx/conf.d/default.conf
COPY ./dist/apps/ui /usr/share/nginx/html

ENV PORT=4200
EXPOSE ${PORT}

CMD nginx -g 'daemon off;'
