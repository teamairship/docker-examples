# start with base Ruby image from Docker Hub
FROM ruby:3.0.1

# install various tools/libraries needed for the application to run successfully
RUN apt update -qq && apt install -y nodejs npm postgresql-client
RUN npm install --global yarn

# set '/app' as our working directory for the rest of the build process
WORKDIR /app

# copy Gemfile and Gemfile.lock over into the image and bundle install
COPY Gemfile Gemfile.lock /app/
RUN bundle install

# copy package.json and yarn.lock
COPY package.json yarn.lock /app/
RUN yarn install --check-files

# copy the rest of the application code over into the image
COPY . /app

# precompile assets and webpacks - needed for production environment
RUN rails assets:precompile

# start the container by running puma using puma.rb config file
CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]