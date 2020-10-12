FROM nginx:latest

COPY configurations/nginx.conf /etc/nginx/nginx.conf
COPY configurations/default.conf /etc/nginx/conf.d/default.conf

# Start nginx and cron as a service
CMD nginx -g 'daemon off;'
