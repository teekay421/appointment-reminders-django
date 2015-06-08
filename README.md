# Appointment Reminders (Django)

Use Twilio to create automatic appointment reminders for your business's clients.

## Quickstart

### Heroku

This project is preconfigured to run on Heroku. Deploy it now:

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/atbaker/appointment-reminders-django)

### Local development

This project is built using the [Django](https://www.djangoproject.com/) web framework. It runs on Python 2.7+ and Python 3.4+.

To run the app locally, first clone this repository and `cd` into its directory. Then:

#. Create a new virtual environment:
    - If using vanilla [virtualenv](https://virtualenv.pypa.io/en/latest/), run `virtualenv venv` and then `source venv/bin/activate`
    - If using [virtualenvwrapper](https://virtualenvwrapper.readthedocs.org/en/latest/), run `mkvirtualenv appointments`
#. Install the requirements with `pip install -r requirements.txt`
#. Start a local PostgreSQL database and create a database called `appointment_reminders`
    - If on a Mac, I recommend [Postgres.app](http://postgresapp.com/). After install, open psql and run `CREATE DATABASE appointment_reminders;`
    - If Postgres is already installed locally, you can just run `createdb appointment_reminders` from a terminal
#. Run the migrations with `python manage.py migrate`
#. Optionally create a superuser so you can access the Django admin: `python manage.py createsuperuser`
#. Start the development server: `python manage.py runserver`

This project uses [Celery](http://docs.celeryproject.org/en/latest/index.html) to asynchronously send SMS reminders to users. To start the Celery process:

#. This project uses [Redis](http://redis.io/) as its task queue. Install and start Redis
#. Start a new terminal session and activate your virtual environment
#. Start the Celery worker with the command: `celery -A appointments.settings worker -l info`

You can then visit the application at [http://localhost:8000/](http://localhost:8000/).
