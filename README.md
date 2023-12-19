## Django-React sample/start project
---
 ### Deploying to Railway
     - open Railway UI
     - add new project
     - add postgres as database
     - set variables: SECRET_KEY, DATABASE_URL
     - go to settings
     - generate domain
       - deploy > custom start command > ``` gunicorn.wsgi --log file - ```
       - build > custom build command > ``` CI=false react-scripts build ```
     - set DOMAIN_NAME variable then (config/settings.py):
       - add the domain to ALLOWED_HOST
       - add url to CSRF_TRUSTED_ORIGINS
### Deploying to Heroku
     - open Heroku UI
     - ``` $ cd <project-name> ```
     - ``` $ heroku login ```
     - ``` $ heroku git:remote <project-name> ```
     -  If heroku does not support the python version which you would like to use in runtime.txt then ignore the file (.slugignore) and use the default on the platform.
     - ``` $ git push heroku main ```
     -  overview > heroku postgres > settings > database credetentials
     -  copy URI to DATABASE_URL variable in config vars
     - ``` $ heroku run python manage.py migrate ```