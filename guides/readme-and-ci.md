Once a project has been created at Github, the next step is to prepare its most basic documentation (README file) and integrate it into a continuous building cycle.   

Before starting to edit the README file, we must first register the project in some external services to automate its construction:

## Continuous Integration
1. Go to [travis-ci.org](https://travis-ci.org) and sign up with your Github account.
1. Accept the Authorization of Travis CI. You’ll be redirected to GitHub.
1. Click the green Activate button, and select the repository (i.e. the new github project) you want to use with Travis CI.
1. Add a `.travis.yml` file to your repository to tell Travis CI what to do. The following example specifies a Java project that should be built with Java 8.x.
```yml
language: java
jdk:
  - openjdk8
```
1. Add the `.travis.yml` file to git, commit and push to trigger a Travis CI build. Travis only runs builds on the commits you push after you’ve added a `.travis.yml` file.
1. Check the build status page to see if your build passes or fails according to the return status of the build command by visiting Travis CI and selecting your repository.

## Continuous Delivery
[jitpack.io](https://jitpack.io) is a package repository for Gradle, Maven, Sbt and Leiningen projects. It builds Git projects on demand and provides you with ready-to-use artifacts (jar, aar).  
1. Go to [jitCI.com](https://jitci.com/) and sign in with your Github account.
1. Add your repository (i.e the new github project)
1. Add a `jitpack.yml` file to your repository to tell JitPack some specific requirements.
1. Add the `jitpack.yml` file to git, commit and push before to trigger a Jitpack build. The following example specifies a Java project that should be built with java 8.
```yml
jdk:
  - openjdk8
```
1. Create a GitHub [release](https://help.github.com/en/articles/creating-releases) to trigger a Jitpack build.
1. Add dependency information in your README. Tell the world where to get your library.

## Continuous Deployment
[travis-ci.org](https://travis-ci.org) supports continuos deployment to the following providers: AWS S3, AZURE WEB APPS, BINTRAY, GITHUB PAGES, GITHUB RELEASES, GOOGLE APP ENGINE, HEROKU.. take a look [here](https://docs.travis-ci.com/user/deployment) for more information.
1. Add a 'deploy' section in your `.travis.yml` descriptor with the credentials for the deployment. For example, if you want to deploy to both cloudControl and Heroku, your `deploy` section would look something like this:
```yml
deploy:
  - provider: cloudcontrol
    email: "YOUR CLOUDCONTROL EMAIL"
    password: "YOUR CLOUDCONTROL PASSWORD"
    deployment: "APP_NAME/DEP_NAME"
  - provider: heroku
    api_key: "YOUR HEROKU API KEY"
```

## Basic Documentation - Readme file
Once the project has been incorporated in the continuous integration services, we can create the `README.md` file:
1. Copy the [template](https://github.com/TBFY/general/blob/master/templates/README-template.md) file to your repository and renamed it to `README.md`.
1. Replace `PROJECT-NAME` with the name of your project at Github.
1. A logo is required, so add a `logo.png` file to your repository.
1. Add the main features of your project into the `Basic Overview` section.
1. Add the steps to complete a fully operational basic use-case into `Quick Start` section. If you need to include more information create links from here. The extension of the README file must be small.
1. If Jitpack was used, add the repository information associated with the artifact created in the project into `Last Stable Release` section. Otherwise links to the last release generated in Github.


Take a look at these examples for inspiration:
* [Harvester](https://github.com/TBFY/harvester)
* [Search-API](https://github.com/TBFY/search-API)
