# Itinerar

Trip planning and mis-spelling stuff

[![Built with Cookiecutter Django](https://img.shields.io/badge/built%20with-Cookiecutter%20Django-ff69b4.svg?logo=cookiecutter)](https://github.com/cookiecutter/cookiecutter-django/)
[![Black code style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

## Getting started

1. `pre-commit install`
2. `make deploy-local`

## Settings

Moved to [settings](http://cookiecutter-django.readthedocs.io/en/latest/settings.html).

## Basic Commands

### Setting Up Your Users

-   To create a **normal user account**, just go to Sign Up and fill out the form. Once you submit it, you'll see a "Verify Your E-mail Address" page. Go to your console to see a simulated email verification message. Copy the link into your browser. Now the user's email should be verified and ready to go.

-   To create an **superuser account**, use this command:

        $ python manage.py createsuperuser

For convenience, you can keep your normal user logged in on Chrome and your superuser logged in on Firefox (or similar), so that you can see how the site behaves for both kinds of users.

### Type checks

Running type checks with mypy:

    $ mypy itinerar

### Test coverage

To run the tests, check your test coverage, and generate an HTML coverage report:

    $ coverage run -m pytest
    $ coverage html
    $ open htmlcov/index.html

#### Running tests with pytest

    $ pytest

### Live reloading and Sass CSS compilation

Moved to [Live reloading and SASS compilation](http://cookiecutter-django.readthedocs.io/en/latest/live-reloading-and-sass-compilation.html).

### Celery

This app comes with Celery.

To run a celery worker:

``` bash
cd itinerar
celery -A config.celery_app worker -l info
```

Please note: For Celery's import magic to work, it is important *where* the celery commands are run. If you are in the same folder with *manage.py*, you should be right.

## Deployment

The following details how to deploy this application.

### Docker

See detailed [cookiecutter-django Docker documentation](http://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html).

## TODOs

- [ ] The local and production dockerfiles should be unified as much as possible
- [ ] local dev inside docker containers
- [ ] Production deploy to ECS
    * https://github.com/Andrew-Chen-Wang/cookiecutter-django-ecs-github
    * https://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html
    * https://benjlindsay.com/posts/deploying-a-cookiecutter-django-site-on-aws
    * https://kandi.openweaver.com/python/Andrew-Chen-Wang/cookiecutter-django-ecs-github
    * https://treeschema.com/blog/comprehensive-ecs-deployments-database-and-ecs-deploy/ (this one)
- [ ] pre-commit stuff should be in docker containers and not rely on stuff on a given host
- [x] rename the containers. They are just `node` and `django` etc...
- [ ] Figure out database connection stuff. How does it work locally, and swap out docker for RDS in prod
    * It's doing some default stuff to connect to 5432. That'll collide with other projects as it's the default port for postgres
- [ ] Basic repo hygeine :smh:... Get rid of the .env files
- [ ] What is merge_production_dotenvs_in_dotenv.py doing?
- [ ] Figure out how to use flower
- [ ] Figure out what manage.py is all about
