FROM node:12-alpine3.14
MAINTAINER doh<@sdmkjz.cn>

VOLUME ["/app"]
WORKDIR /app

RUN apk add git && \
npm install -g hexo-cli && \
npm install hexo-deployer-git --save && \
npm i hexo-permalink-pinyin --save && \
npm i --save hexo-wordcount


ENV HEXO_SERVER_PORT=4000

EXPOSE 4000
CMD ["/bin/sh","-c","if [ \"$(ls -A /app)\" ]; then     echo \"***** App directory exists and has content, continuing *****\" && hexo clean && hexo g; else     echo \"***** App directory is empty, initialising with hexo and hexo-admin *****\" &&     hexo init;   fi; echo \"***** Starting server on port ${HEXO_SERVER_PORT} *****\" &&   hexo server -d -p ${HEXO_SERVER_PORT}"]
