# Circulate - Demo App for CircleCI

[![CircleCI](https://circleci.com/gh/keybits/circulate.svg?style=svg&circle-token=73c3707a68357dbe9a2cab42145291ce1840133d)](https://circleci.com/gh/keybits/circulate)

This is a working application that you can use to learn how to build, test and deploy with CircleCI 2.0. Follow the [Project Walkthrough](https://circleci.com/docs/2.0/project-walkthrough/) guide here.

It's a 'social blogging' web application similar to Twitter. Users can create accounts, make posts, follow users and comment on posts. You can *circualate* your thoughts and ideas :-)

**Original Author Credit:** This is directly based on Miguel Grinberg's excellent [Flasky](https://github.com/miguelgrinberg/flasky) application.

The application uses Python and Flask for the backend.

**IMPORTANT:**

- You **do not need to know Python to follow the guide** in the CircleCI docs.
- You will not need to install or setup a Python environment to follow the tutorial - you can follow along by making edits to config on GitHub if you wish.
- No matter what language or stack you are going to use with CircleCI, we recommend following the walkthrough first, as it introduces concepts about CircleCI that you can then apply to your own project.

## Running locally

**Note:** As mentioned above you don't need to run this application locally to learn about using CircleCI.

- Install PostgreSQL (tested with 9.6.2)
- Install Python (tested with Python 3.6)
- Fork or clone this repository
- Create and activate a virtual environment
- Enter the following commands:

```
createdb circulate
pip install -r requirements/dev.txt
python manage.py db init
python manage.py db migrate
python manage.py db upgrade
```

then:

```
python manage.py shell
```

and run the following command to set up Roles:

> Role.insert_roles()
> User.add_self_follows()

## Tests

The app runs various tests:

- unit tests for database models (using unittest)
- unit tests for client view functions (using Flask Test Client)
- unit tests for the API (using Flask Test Client)
- integration tests for logging in etc (using Selenium and ChromeDriver)

It uses [unittest-xml-reporting](https://github.com/xmlrunner/unittest-xml-reporting) for JUNIT style report generation.

See the `tests` directory for details.

`python manage.py test` to run the tests locally.


## TODO

- add parallelization
- deploy to Heroku

- test with multiple python versions
- run with coverage on CircleCI
- add coverage badge to README

- make email testing work on CircleCI with mailhog
