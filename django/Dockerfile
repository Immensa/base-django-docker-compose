FROM python:3.8.5-alpine3.12

ENV PYTHONUNBUFFERED=1

WORKDIR /usr/src/app

COPY requirements.txt ./

RUN \
 apk add --no-cache postgresql-libs && \
 apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev && \
 python3 -m pip install -r requirements.txt --no-cache-dir && \
 apk --purge del .build-deps

COPY . .

RUN pip install --upgrade pip

RUN pip install -r requirements.txt