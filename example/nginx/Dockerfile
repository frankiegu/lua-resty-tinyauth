FROM openresty/openresty:alpine AS builder
RUN apk --no-cache add curl perl
RUN /usr/local/openresty/bin/opm get pintsized/lua-resty-http

FROM openresty/openresty:alpine
COPY --from=builder /usr/local/openresty/site /usr/local/openresty/site
COPY example/nginx/nginx.conf /etc/nginx/nginx.conf
COPY lib/resty/tinyauth.lua /usr/local/openresty/site/lualib/resty/tinyauth.lua

COPY example/nginx/*.js /srv/static/

CMD ["nginx", "-c", "/etc/nginx/nginx.conf"]
