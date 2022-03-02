# AWS-integration
Description of how to integrate an Angular (or any other) web app with AWS CI/CD pipelines

## before starting


### Create a new web app or use an existing one
For this eample I will be using a Tic Tac Toe app I have created previously with:
```sh
ng create __app-name__ 
```
### add a yaml file

before deployign yiour app you need a buildspec.yaml file in your root directory

It should look something like below
```sh
version: 0.1

phases:
  install:
    commands:
      - echo installing nodejs...
      - curl -sL https://deb.nodesource.com/setup_14.x | bash -
      - apt-get install -y nodejs
  pre_build:
    commands:
      - echo installing dependencies...
      - npm i -g @angular/cli
      - npm install --save-dev @angular/cli@latest
      - npm install
  build:
    commands:
      - echo building...
      - ng build --prod
artifacts:
  files:
    - "**/*"
  discard-paths: no
  base-directory: "dist/aws-test-app*"
```

## Amplify 
### Open [Amplify](https://console.aws.amazon.com/amplify/home)
- Click "get started"
- Click "get started" again under Amplify Hosting
- Connect your git repo 
- Select Repository and branch
- 




