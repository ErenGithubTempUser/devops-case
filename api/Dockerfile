FROM ruby:2.5.5-buster

USER root

RUN apt update
RUN apt install ruby build-essential ruby2.5-dev postgresql-server-dev-all -y

WORKDIR /api

COPY . .

RUN useradd -m appuser

USER appuser

COPY --chown=appuser . ./

RUN gem install bundler -v 2.2.30
RUN bundle install