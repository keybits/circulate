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

## Deployment to Heroku

The application demonstrates how to deploy to Heroku from CircleCI 2.0. Please consult the [Project Walkthrough](https://circleci.com/docs/2.0/project-walkthrough/) for documentation on how this works.

## Running locally

**Note:** As mentioned above you don't need to run this application locally to learn about using CircleCI.

- Install PostgreSQL (tested with 9.6.5)
- Install Python (tested with Python 3.6.2)
- Fork or clone this repository
- Create and activate a virtual environment
- Enter the following commands:

```
createdb circulate
pip install -r requirements/dev.txt
python manage.py deploy
python manage.py runserver
```

You can now test the app locally with the Flask development server.

## First run on Heroku

```
heroku create circulate
heroku addons:create heroku-postgresql:hobby-dev
set: heroku config:set FLASK_CONFIG=heroku
git push heroku master
heroku run python manage.py deploy
heroku restart
```

Note: 

- you need a local copy of migrations > versions > xxx.py that is pushed to heroku
- take care to delete session cookies if changing between py 2 and 3!

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

- test with Firefox and Geckodriver (working with FirefoxNightly locally - see firefox-geckodriver-local branch) - on CircleCI I'd need Firefox nightly (or a firefox nightly docker container) which is version 57 at the time of writing. When FF 57 is out we should be good to go.
- test with Headless Chrome
- cache heroku toolbelt installation on CircleCI - needs an 'if not' for the directory it's installed to
- add parallelization (different branch)
- add workflow examples (different branch)
- test with multiple python versions
- run with coverage on CircleCI
- make email testing work on CircleCI with mailhog
- make email work on the deployed Heroku app
