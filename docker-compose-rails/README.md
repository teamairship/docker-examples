# RAILS DOCKER COMPOSE EXAMPLE

- Run `docker compose up`
    - This builds entire system the first time it is ran
    - You would normally want an env vars file outside of the code repository, for convenience one is provided here in the project root `.env-vars`

- In another terminal window run
    - `docker compose run web rails db:create`
    - `docker compose run web rails db:migrate`
    
- If changes are made to `Gemfile`, `Dockerfile`, or `docker-compose.yml`, then run `docker compose build` to pull in those changes