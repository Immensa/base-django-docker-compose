FROM python:3.8.5-alpine3.12

#Python

ENV PYTHONUNBUFFERED=1

WORKDIR /usr/src/app

COPY requirements.txt ./

RUN apk add --update g++ gcc git tcpdump libffi-dev libc-dev

RUN apk add --no-cache --virtual .build-deps git autoconf automake flex bison libtool pkgconf make libxslt-dev musl-dev linux-headers  && \
    apk add --no-cache libxslt py3-lxml bash tzdata musl && \
    apk del --no-cache .build-deps && \
    apk add --no-cache py3-requests && \
    rm -rf /var/cache/apk/*

RUN apk add --no-cache --update postgresql-dev

RUN apk add --no-cache --update jpeg-dev zlib-dev libjpeg libwebp-dev

RUN pip install --upgrade pip

RUN pip install wheel
RUN pip install pyopenssl
RUN pip install Pillow
RUN pip install psycopg2

RUN pip install -r requirements.txt --no-cache-dir

COPY . .