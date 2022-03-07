# AWS-integration
Description of how to integrate an Angular (or any other) web app with AWS CI/CD pipelines

## before starting


### Create a new web app or use an existing one
For this example I will be using a Tic Tac Toe app I have created previously with:
```sh
ng create __app-name__ 
```
### add a yaml file

before deploying your app you need a buildspec.yaml file in your root directory

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
- Click "get started" under Amplify Hosting ![get started](/amplify-get-start-app.png)
- Connect your git repo 
- Select Repository and branch ![connect](/connect-github-test-branch.png)
- configure build options (.yaml file we created earlier) ![yaml](![connect](/configure-build-settings-web.png)
- save and depoly ![deploy](/finish-app-settings-deploy.png)

### that's it! 
after this feel free to configure other settings in the App management console like adding a testing enviroment, adding a costom domain or adding tests. 




