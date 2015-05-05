FROM ruby:2.2

# throw errors if Gemfile has been modified since Gemfile.lock
#RUN bundle config --global frozen 1

# create tdiary directory
RUN mkdir -p /usr/src/app
RUN gem install tdiary
RUN tdiary new --skip-bundle /usr/src/app
WORKDIR /usr/src/app

# install libraries
COPY Gemfile.local /usr/src/app/
RUN bundle --without=development:test:coffee --jobs=4 --retry=3

# FIXME: id=user pass=user
COPY dot.htpasswd /usr/src/app/.htpasswd

# FIXME: avoid bug
RUN rm -f /usr/local/bundle/bundler/gems/tdiary-core-a875dae9543c/lib/tdiary/plugin/90migrate.rb

VOLUME /usr/src/app/data
EXPOSE 9292
CMD [ "bundle", "exec", "rackup" ]
