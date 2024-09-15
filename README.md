# GeoDjango
This setup allows you to quickly set up a development environment for a Django project using Docker. The stack includes:
- Django (backend)
- PostgreSQL (database)
- Nginx (reverse proxy)
  
# Prerequisites
Make sure you have installed:
- Docker
- Docker Compose

## Cloning the repo and starting app

1. Create virtual enviroment in your directory:
```
python3 -m venv venv
```
2. Clone the repo to your directory:
```
git clone https://github.com/MurCezary/GeoDjango.git
```
3. Start virtual enviroment:
```
. venv/bin/activate
```
5. Change the .env file:
Change SECRET_KEY, DJANGO_ALLOWED_HOSTS, POSTGRES_PASSWORD, DJANGO_SUPERUSER_USERNAME etc, 
Please do not use bracketc, colons, spaces etc
DJANGO_ALLOWED_HOSTS should be separated by ','
```
.env/

DEBUG=False
SECRET_KEY=django_seceret_key_generated
DJANGO_ALLOWED_HOSTS=localhost,127.0.0.1,web 
POSTGRES_ENGINE=django.db.backends.postgresql
POSTGRES_DB=postgis_db
POSTGRES_USER=app
POSTGRES_PASSWORD=password_to_db
POSTGRES_HOST=db
POSTGRES_PORT=5432
DJANGO_SUPERUSER_USERNAME=your_admin
DJANGO_SUPERUSER_PASSWORD=your_admin_password
DJANGO_SUPERUSER_EMAIL=your_admin_mail
```
6. Build and run the application using Docker Compose::
```
docker-compose up --build
```
This will:

Build the necessary Docker images for Django, PostgreSQL, and Nginx.
Start all services as defined in the docker-compose.yml.

9. Once the application is running, you can access Django at http://localhost:80 or the port set in your nginx/nginx.conf file on line: listen 80;.

10. To stop and remove the running containers use:
```
docker-compose down
```

# Development
You can access the Django shell or run management commands within the running container using:
```
docker-compose exec web python manage.py shell
```

or for example run tests:
```
docker-compose exec web python manage.py test
```
