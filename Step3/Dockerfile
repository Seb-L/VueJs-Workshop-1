FROM kkarczmarczyk/node-yarn:7.6

RUN mkdir -p /vuejs && mkdir -p /vuejs/src
ADD ./ /vuejs
RUN cd /vuejs && yarn

ENV NODE_ENV development

EXPOSE 8080

WORKDIR /vuejs

CMD npm run dev
