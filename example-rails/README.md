# RAILS DOCKER COMPOSE EXAMPLE

- Run `docker compose up`
    - This builds entire system the first time it is ran
    - You would normally want an env vars file outside of the code repository, for convenience one is provided here in the project root `.env-vars`


- In another terminal window run
    - `docker compose run web rails db:create`
    - `docker compose run web rails db:migrate`

    
- If changes are made to `Gemfile`, `Dockerfile`, `package.json`, or `docker-compose.yml`, then run `docker compose build` to pull in those changes


- *NOTE* - This is somewhat of a mixed example. The assets:precompile step is included inside `Dockerfile` as a reminder to use it in a production Dockerfile. However, because the local app directory is being mapped into the docker compose services in `docker-compose.yml` you will need to run similar commands while doing local development to have them show up inside the docker compose service
    - `bundle install`
    - `yarn install`
    - `rails assets:precompile`