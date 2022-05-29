FROM nginx:1.20

ARG node_ver=14.15.1
ARG node_path=/usr/local/lib/nodejs
ARG node_file_name=node-v${node_ver}-linux-x64

ENV PATH ${node_path}/${node_file_name}/bin:$PATH

RUN apt-get update \
  && apt-get install -y ca-certificates curl xz-utils \
  && curl https://nodejs.org/dist/v${node_ver}/${node_file_name}.tar.xz > ${node_file_name}.tar.xz \
  && mkdir -p $node_path \
  && tar xJvf ${node_file_name}.tar.xz -C $node_path

WORKDIR /data

ENV TZ=UTC

COPY ./infra/docker/nginx/*.conf /etc/nginx/conf.d/