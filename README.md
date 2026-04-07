# RENDER DJANGO EXAMPLE

Proyecto de ejemplo de despliegue de proyecto Django en Render.

## Configuración de variables de entorno.

```
SECRET_KEY=dfasdfsdafdsafdsdfd
DB_NAME=render_db_93rc
DB_USER=render_user
DB_PASSWORD=UG0dKqQ3UTdldCSLDOAGoUIw099q8nyc
DB_HOST=dpg-d764lvua2pns738acq70-a.oregon-postgres.render.com
```

## Configuración Build & Deploy 

Repository:         https://github.com/elprofecarreno/render_django_example

Build Command:      pip install -r requirements.txt && python manage.py collectstatic --noinput && python manage.py migrate && python manage.py shell -c "from django.contrib.auth import get_user_model; U=get_user_model(); u='admin'; e='admin@admin.com'; p='admin'; U.objects.filter(username=u).exists() or U.objects.create_superuser(u,e,p)"

Start Command:      gunicorn render_django_example.wsgi:application --bind 0.0.0.0:$PORT


## Comando local.

```
virtualenv env
source env/bin/activate
pip install -r requirements.txt && python manage.py collectstatic --noinput && python manage.py migrate && python manage.py shell -c "from django.contrib.auth import get_user_model; U=get_user_model(); u='admin'; e='admin@admin.com'; p='admin'; U.objects.filter(username=u).exists() or U.objects.create_superuser(u,e,p)"
gunicorn render_django_example.wsgi:application --bind localhost:8000
```

http://localhost:8000
