FROM node:14.0.0 AS compile-image

RUN npm install -g @angular/cli@10.0.8

WORKDIR /opt/ng

COPY /hello-angular .

RUN npm install

RUN ng build --prod


FROM nginx
# COPY docker/nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=compile-image /opt/ng/dist/hello-angular /usr/share/nginx/html
