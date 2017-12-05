# herokuUsefulCommands
A list of some useful commands for Heroku.

## Download heroku client (MacOs): 
- `brew install heroku/brew/heroku`

## Login to heroku client: 
- `heroku login`

## Create heroku app: 
- `heroku create --stack cedar`

## Set heroku buildpack for grails app: 
- `heroku buildpacks:set https://github.com/heroku/heroku-buildpack-grails`

## Rename heroku app:
- `heroku apps:rename NEWNAME`

## Especify app JDK version:
- `echo "java.runtime.version=1.8" > system.properties`
- `git add system.properties`
- `git commit -m "JDK 8"`
- `git push`

## Add MySql DB service: 
- `heroku addons:create jawsdb`

## Configure MySql DB connection with Heroku: 
-  `heroku config -s | grep JAWSDB_URL >> .env`
-  `$ more .env`
-  Add `.env` file to `.gitignore`
-  Add DB connection string in your app: 
-    `dbCreate = "update"`
-    `URI jdbUri = new URI(System.getenv("JAWSDB_URL"))`
-    `driverClassName = "com.mysql.jdbc.Driver"`
-    `username = jdbUri.getUserInfo().split(":")[0]`
-    `password = jdbUri.getUserInfo().split(":")[1]`
-    `port = String.valueOf(jdbUri.getPort())`
-    `url = "jdbc:mysql://" + jdbUri.getHost() + ":" + port + jdbUri.getPath()`

## Deploy heroku app: 
- `git push heroku master`

## View heroku app logs: 
- Send logs to stdout
- `heroku logs --tail`

## Push to remote repository:
- `heroku git:remote -a HEROKU_APP_NAME`
