#pull base linux image
FROM python:3.12.5-alpine3.20

# set work directory and environment variables
ENV HOME=/home/app
ENV APP_HOME=/home/app/web
RUN mkdir $HOME
RUN mkdir $APP_HOME
RUN mkdir $APP_HOME/staticfiles
RUN mkdir $APP_HOME/mediafiles
#RUN mkdir $APP_HOME/staticfiles
WORKDIR $APP_HOME

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

#install required packages
RUN apk update && \
    apk add --no-cache musl-dev libpq-dev gcc
RUN pip3 install --upgrade pip

# install dependencies
COPY ./requirements.txt .
RUN pip3 install -r requirements.txt

# copy project
COPY . $APP_HOME
