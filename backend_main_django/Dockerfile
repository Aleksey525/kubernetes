FROM python:3.9-slim
ENV PYTHONDONTWRITEBYTECODE 1

WORKDIR /webapp
COPY requirements.txt /webapp/
RUN apt update && apt install -y python3-pip                                  \
    && pip3 install -r requirements.txt                                       \
    && apt remove -y python3-pip                                              \
    && apt autoremove --purge -y                                              \
    && rm -rf /var/lib/apt/lists/* /etc/apt/sources.list.d/*.list
COPY unit_config.json /docker-entrypoint.d/
COPY src /webapp/src
WORKDIR /webapp/src
EXPOSE 80
VOLUME ["/media"]
