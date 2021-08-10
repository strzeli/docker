FROM node:latest

ARG PGID=1000
ARG PUID=1000
ENV PUID ${PUID}
ENV PGID ${PGID}

#RUN groupadd -g ${PGID} user 
#RUN useradd -l -u ${PUID} -g user -m user

#USER user

RUN usermod -o -u 1000 -g 1000 node
USER node

