FROM python:3.8.5-alpine3.12

ENV PYTHONUNBUFFERED=1

WORKDIR /usr/src/app

COPY requirements.txt ./

RUN \
 apk add --no-cache postgresql-libs linux-headers libffi-dev libc-dev && \
 apk add --no-cache --virtual .build-deps gcc musl-dev musl postgresql-dev && \
 apk --purge del .build-deps

RUN apk add --no-cache --update jpeg-dev zlib-dev libjpeg libwebp-dev

RUN pip install --upgrade pip

RUN pip install wheel
RUN pip install pyopenssl
RUN pip install Pillow

RUN pip install -r requirements.txt --no-cache-dir

COPY . .