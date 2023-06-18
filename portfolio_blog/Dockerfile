FROM python:alpine

#set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# updates and modules
RUN apk update && apk add libpq
RUN apk add --virtual .build-deps gcc python3-dev musl-dev postgresql-dev

# pip update
RUN pip install --upgrade pip

# install packages for project
COPY requirements.txt ./requirements.txt
RUN pip install -r requirements.txt

WORKDIR /app

RUN apk del .build-deps

COPY . .

RUN chmod -R 777 ./
