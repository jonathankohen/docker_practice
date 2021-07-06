# Docker Practice

Working example of using Docker with Django!

## Installation

This Django application needs [Pipenv](https://pypi.org/project/pipenv/) to run properly.

At the root of the file, please run:

`pipenv shell`

`pipenv install`

## Setup

### Create .env

Please add a `.env` file at the root of the project with the following content (added here for the sake of demonstration, these should of course be private!)

```markdown
DEBUG=1
SECRET_KEY="lo_tc@i%vo=+6\*^#klf3rodt3x45!5e=d893=609rl\*!t6jx$5"
```

### Django DB, superuser

```python
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

### Test Gunicorn

```sh
gunicorn dock.wsgi:application --bind 0.0.0.0:8888
```

Upon success, the following is displayed:

```sh
[2021-07-06 17:24:45 -0400] [22014] [INFO] Starting gunicorn 20.1.0
[2021-07-06 17:24:45 -0400] [22014] [INFO] Listening at: http://0.0.0.0:8888 (22014)
[2021-07-06 17:24:45 -0400] [22014] [INFO] Using worker: sync
[2021-07-06 17:24:45 -0400] [22015] [INFO] Booting worker with pid: 22015
```

Go ahead and visit `losthost:8888` and have a look! The Django default landing page should be presented.

`^c` to exit.

## Running Docker

`docker build -t <CUSTOM_TAG_NAME> -f Dockerfile .`

`docker run -it -p 8888:8888 <CUSTOM_TAG_NAME>`

Check out `losthost:8888` again, the default Django landing page should be presented. This may take a second.

`^c` to exit.

## Alternatively

To run continously in the background:

`docker build -t <CUSTOM_TAG_NAME> -f Dockerfile .`

`docker run -it -d -p 8888:8888 <CUSTOM_TAG_NAME>`

Check out `losthost:8888` again, the default Django landing page should be presented. This may take a second.

`docker ps` (find the ID of the container)

`docker stop <ID>`

`docker rm <ID>`
