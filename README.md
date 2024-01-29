## Django-React template/start project

 ### Local development
 ---
- Download the zip file
- Create your own virtual environment on your project directory and install the required libraries/packages. (pipenv) 

  - ```$ pipenv install -r requirements.txt```

- Create postgres database on your local system

  - ``` # Download & install postgres ```
  - ``` psql -U postgres ```
  - ``` CREATE DATABASE <db_name> WITH OWNER postgres; ```

- Create .env file that includes DEBUG, SECRET_KEY, SSL_REQUIRE, DATABASE_URL values

  - ``` # Generate secret key ```
  - ``` $ python -c 'import secrets;print(secrets.token_urlsafe())' ```
  - ``` DATABASE_URL=postgres://postgres:<password>@localhost:5432/<database> ```

- Migrate the models to database & run collectstatic for the static files

  - ``` $ pipenv shell ```
  - ``` $ python manage.py migrate ```
  - ``` $ python manage.py collectstatic --noinput ```

- Install node modules and build

  -  ``` $ npm install ```
  -  ``` $ npm run build ```
    
- Run on localhost
  -  ``` $ python manage.py runserver ```
  
- Initialize your own git repo and commit/push to github
 ### Deploying to Railway
 ---
 - Open Railway UI
 - Add new project
 - Add postgres as database
 - Set variables: SECRET_KEY, DATABASE_URL
 - Go to settings
 - Generate domain
 - Deploy > custom start command > ``` gunicorn.wsgi --log file - ```
 - Build > custom build command > ``` CI=false react-scripts build ```
 - Set DOMAIN_NAME variable then (config/settings.py):
   - Add the domain to ALLOWED_HOST
   - Add url to CSRF_TRUSTED_ORIGINS
- Create a nixpacks.toml file  > ``` providers = ["node", "python"] ```
### Deploying to Heroku
---
- Open Heroku UI
- ``` $ cd <project-name> ```
- ``` $ heroku login ```
- ``` $ heroku git:remote <project-name> ```
- If heroku does not support the python version which you would like to use in runtime.txt then ignore it (.slugignore) and use the default on the platform.
- ``` $ git push heroku main ```
- Overview > heroku postgres > settings > database credentials
- Copy URI to DATABASE_URL variable in config vars
- ``` $ heroku run python manage.py migrate ```
 
