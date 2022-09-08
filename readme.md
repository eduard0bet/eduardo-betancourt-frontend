# Eduardo Betancourt - AWS Devops Test

Dear Scopic Thanks for the opportunity.

I clone the project and run it first on my PC to know the dependencies we need to use.

## Installation
We use a t3.micro EC2 instance on AWS for testing for each project (backend and frontend)
in a correct way we can create Monorepo with tools like TurboRepo, that can help us with the use of just one Instance, make a dockerized environment and will be more efficient and easy to mintain.

## Installation - Deployment (Backend)
```bash
PUBLIC URL
http://ec2-13-49-148-3.eu-north-1.compute.amazonaws.com:8080/
```
Due to the outdated is the project I have to install via NVM using NODE v12 to flawless work


```bash
nvm install 12 && nvm use 12
```
After this i run a simply 
```bash
npm install
```
```bash
npm run start
```
## IMPORTANT
We need to configure the access to our new DB, in this case, I'm using AWS RDS (eu-north-1) with a small db.t3.micro, this will help to lowcost on startup.

```javascript
/**
*localhost.js | production.js config files
**/
  database: {
    username: 'postgres',
    dialect: 'postgres',
    password: 'tesdb3091*!1',
    database: 'ebdb1',
    host: 'eduardo-betancourt-db1.ceywtl6l9sjq.eu-north-1.rds.amazonaws.com',
    logging: console.log,
  },
```
i Use a localhost enviroment in this project cuz is a dev-test enviroment.
 

```bash
> simple-inventory-app-backend@ start /Users/eduardobet/Projects/eduardo-betancourt-simple-inventory-app/backend
> cross-env NODE_ENV=localhost nodemon ./server.js

[nodemon] 1.19.4
[nodemon] to restart at any time, enter `rs`
[nodemon] watching dir(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node ./server.js`
Listening on port 8080
```
## Installation - Deployment (Frontend)
```bash
PUBLIC URL
http://ec2-13-49-158-206.eu-north-1.compute.amazonaws.com:3000/
```
On this side no issue with Updates, React Apps are more easy to update and runnit with more updated versions of NodeJs.

In MacOs (Apple Silicon) nodejs from 14 to last versions works ok, so i have to use NODE16 on this one.

We Use another instance on EC2 same t3.micro will be easy to scale and we can use tools like CLOUDWATCH and create notifications that can use more resources to run greate with more and more conections.

```bash
npm install
```
```bash
npm run start
```
We check the config file and update the URL of the API(our backend) 
in this case i dont use .ENV files, but we can configure and make more efficient the work on this side.


```javascript
/*localhost.js | production.js */

const backendUrl = `http://ec2-13-49-148-3.eu-north-1.compute.amazonaws.com:8080/api`;

export default {
  backendUrl,
};

```

```bash
Compiled successfully!

You can now view app-frontend in the browser.

  Local:            http://localhost:3000/
  On Your Network:  http://192.168.1.124:3000/

Note that the development build is not optimized.
To create a production build, use npm run build.


```

## Actually there is no CI CD tools running on this case, I would like to use the same as amazon in this one (CodePipeline and Codeploy) ill be working sometime with Jenkings and Teamcity but due to AWS permission, i cannot advance. I try on Github Actions buy due to the Delay I delivery this way.

The code of project i cloned and uploaded on my Personal Github Account
```bash
Backend
git@github.com:eduard0bet/eduardo-betancourt-backend.git

Frontend
git@github.com:eduard0bet/eduardo-betancourt-frontend.git
```
a .PEM file is attached in this email so you can clone and check.

## THIS UPLOAD, TEST, AND RUNNING ENVIROMENS I MADE IT IN 4 Hours as it is, so this was the most I can achieve in that period of time. with more time we can create a trunk based project, with a complete CI/CD and more efficient Security between Instances and AWS environment.

## Done
Our backend and frontend is running with no issue on 
