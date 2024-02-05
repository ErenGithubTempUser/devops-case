FROM ruby:2.5.5-alpine as base

USER root

RUN apk add postgresql-dev tzdata

FROM base as dependencies 

RUN apk add build-base

COPY Gemfile Gemfile.lock ./

RUN gem install bundler -v 2.2.30
RUN bundle install

FROM base 

RUN adduser -D appuser

USER appuser

COPY --from=dependencies /usr/local/bundle/ /usr/local/bundle/
COPY --chown=appuser . ./
