# This is the based on video lecture of hitesh ch. channel "chai aur code"

## 1. we make a folder and initialize node package manager as
    npm init

 // provide details while intializing npm .. like package name, etc..

 ## we can use https://app.eraser.io/ to make data model, or entity relation model


 ## Now we can initialize git repository
   git init  // initializing git to push and track changes
   git add .   // adding all files in tracking

## Now create new repository on github website in your account. you will get different commands to link with vs code project on git hub page after creating repository.

## to match github standard, we can change branch of code from master to main by command
    git branch -m "main"
## set remote by command
    git remote add origin https://github.com/m-shafiq/pharmacybkend.git

## seting upstream and pushing on github

    git push -u origin main

### Now we will add folder structure for the project, consider following points while making structure

    1. if we use images, we need to store images on server or third party services ( if we are using third party services than we store temporarely on server than upload on third party service i.e. aws, azure, google drive etc, you can upload directly on third party, different approaches are used)
    2. So we need to make folder to make public as temporary storage.
    3. Temporary folders are not pushed or tracked by git , until any file in it. so we make file with name .gitkeep (its convention, you can make any empty file)

### Every files are not pushed on github, to avoid extra load, or that can be available in production environment, or secrets, or development depenendencies etc. so we use .gitignore file
-- there are many sites that generate git ignore file contacts. search for gitignore generator in google
-- try https://mrkandreev.name/snippets/gitignore-generator/

### we need environment variable file, to get environment variables from the system, so we generate file .env

-- as env file is not uploaded on git as git ignore file, if we want to upload it for somereasone like to view who is using repository, so we can make another file like .env.sample,  and paste same code in it, as it is not ignored by gitignore file, so it will be pushed.

### now we need index.js file as we told that index.js file will be started file (while creating nmp init)

-- better way to make folder src (or any, but it is good convention), make file in folder src: index.js, constants.js, app.js

## Now we set/ update package.json file to configure or tell project about start command, etc.

### As two syntax are used to import / link different file (required=>commonjs, module=>import), so we will tell in package.json file what type of syntax we will use, i.e. package (import syntax)

-- we will add   "type": "module", in package.json file

### To handle server start, restart automaticaly on save, New feature is introduced in java "--watch" but it is new and not much used in production, so third party tool is used ilke "Nodemon"
-- nodemon module is used in development that auto restart project on save
-- nodemon is installed as dev dependancy (as it is only used in development not taken to production)

-- to install in development dependancy. npm i -D nodemon

### Now tell what command will be used to start index.js file, with nodemon module

-- add "dev": "nodemon src/index.js"    in scripts section of package.json file.

#### Note : Environment variable and module type import having some problems in production, because .env is using required syntax, to resolve it. ( you can search for dotenv)