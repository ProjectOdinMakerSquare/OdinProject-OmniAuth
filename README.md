# GitHub-Authenticated Rails Application Template

A basic Rails template app with authentication through GitHub.

## Use

Clone it: don't fork it.

## Features

* Rails application with Unicorn as the web server
* Twitter Bootstrap (with SASS)
* Omniauth with GitHub strategy
* [CanCan][cancan] and [Rolify][rolify]
* [Figaro][figaro] for configuration
* SQLite for development, Postgres for production
* Minitest and Minitest/spec
* [Quiet Assets][quiet] and [Better Errors][better]
* [Sendgrid][sendgrid] for email

## Configuration

Create a new GitHub application with the following URLs:

* URL: `http://0.0.0.0:2999/`
* Callback URL: `http://0.0.0.0:2999/auth/github/callback`

Add the following configuration keys to `config/application.yml`:

* `GITHUB_CLIENT_ID`
* `GITHUB_CLIENT_SECRET`

You can also set `GITHUB_SCOPE` to specify the [scope][scope] you want to ask
users for access to.

## Running the application

A Procfile is included for convenient statup with [Foreman][foreman]. Once you
have Foreman installed, simply run:

```bash
foreman start
open http://0.0.0.0:2999/
```

## Deployment

Deployment is simple to Heroku:

```bash
heroku create my-app
heroku config:set \
  GITHUB_CLIENT_ID="..." \
  GITHUB_CLIENT_SECRET="..."
git push heroku master
heroku run bundle exec rake db:migrate
```

[foreman]: http://ddollar.github.com/foreman/
[cancan]: https://github.com/ryanb/cancan
[rolify]: https://github.com/EppO/rolify
[figaro]: https://github.com/laserlemon/figaro
[quiet]: https://github.com/evrone/quiet_assets
[better]: https://github.com/charliesome/better_errors
[sendgrid]: http://sendgrid.com/
[scope]: http://developer.github.com/v3/oauth/#scopes
