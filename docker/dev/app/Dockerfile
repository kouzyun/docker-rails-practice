FROM ruby:3.2.2
ENV APP_ROOT /var/www/app
WORKDIR $APP_ROOT

RUN mkdir -p /var/run/puma
RUN mkdir -p /config
RUN mkdir -p /tmp/sockets

RUN curl https://deb.nodesource.com/setup_12.x | bash
RUN curl https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get install -y --no-install-recommends \
    build-essential \
    libpq-dev \
    locales \
    vim \
    nodejs \
    npm \
    redis-tools \ 
    yarn \
    mariadb-client && \
    rm -rf /var/cache/apt/archives/* /var/lib/apt/lists/*


RUN gem install bundler 
COPY Gemfile Gemfile.lock $APP_ROOT
RUN bundle install

RUN npm install n -g
RUN n 12.18.4
RUN yarn install

EXPOSE 80
CMD ["bundle", "exec", "puma", "-C", "config/puma-socket.rb", "-e", "development"]