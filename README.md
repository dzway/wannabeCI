# WCI - wannabeCI
wannabeCI is a Command Line Interface (CLI) to help your development project that wanna be part of a CI/CD enviroment. WCI help your project to compile in a Container enviroment, so you can test your code locally, before pushes it to your repository, and wait for jenkins to show you that will not compile because you forgot to mentions a dependency that only exists in your local machine global enviroment and etc.

WCI can also be used inside jenkins, so you can set it up to run on your docker slave, to compile any sort of programming language, and killing the container right after it!

## Setup
First you have to install docker on your machine (**Dont worry if you have no idea how**):
>$: wci install --docker
We use get.docker.com script to actually do it, feel free to visit get.docker.com to check it out.


## Run
To run your project with wci tool, go to your project folder and use init to generate wci structure:

> $: wci init


It will create the following folder and files:
```
+-- .ci/
|   +-- build.sh
|   +-- config.json
```
Then you are ready to run:

> $: wci build

It will trigger your compile process inside the container image that is specified inside **config.json**.

## Config
You should change **build.sh** to match your project compile structure:
Example(maven project):
```
!#/bin/bash
echo 'this is a mvn sample project compile script'
mvn clean install
```
Example(nodejs project):

```
!#/bin/bash
echo 'this is a nodejs sample project compile script'
npm install
npm run build
```
You should also change **config.json** to a container image that matches your application.
Example(Maven Project):

```
{
   "Image":"maven:latest"
}
```

Example(nodejs):
```
{
   "Image":"node:latest"
}
```

After this initial configuration, you're good to go, and compile your project in a much easier enviroment, that can also be the same enviroment that your **jenkins** or any other orquestrator uses with a container to compile.

## Issues
This is a independent free project, any issues or improvements, are welcome here: [issues](https://github.com/diztak-ltda/wci/issues).
## Donations
You can also help us out with paypal donations, or even a feedback email:

**EMAIL/PAYPAL ACC**: daniel.yonezawa@live.com
