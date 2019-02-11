FROM node:latest AS build

ENV NODE_ENV production
ENV HOST 0.0.0.0
ENV PORT 80
WORKDIR /web
EXPOSE 3000
EXPOSE 3001
COPY . .
#RUN yarn install
# RUN yarn run build 
# RUN npx pkg . -t node8-alpine-x64 --output web

# FROM alpine:latest
# RUN apk update && \
#     apk add --no-cache libstdc++ libgcc ca-certificates && \
#     rm -rf /var/cache/apk/*

# WORKDIR /web
# COPY --from=build /web/web /web/web

CMD ["/web/razzle-k8s-linux"]