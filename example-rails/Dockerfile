FROM ruby:3.0.1

RUN apt update -qq && apt install -y nodejs npm postgresql-client
RUN npm install --global yarn

WORKDIR /app

COPY Gemfile Gemfile.lock /app/
RUN bundle install

COPY package.json yarn.lock /app/
RUN yarn install --check-files

COPY . /app

RUN rails assets:precompile

CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]