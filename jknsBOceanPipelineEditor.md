# Jenkins Blue Ocean Pipeline Editor #

## Let's make simple Jenkinsfile for pytrhon ##
We use GitHub and we asume that there is
**no Jenkinsfile** in GitHub's repo

In Jenkins:
```
Open Blue Ocean > New Pipeline > GitHub
Which organization does the repository belong to?
```

### If not connected Jenkins to GitHub: ###
  ```
  Create an access token here
  ```
  Other page opens write something in description
  and accept all the default choices:
  ´´´
  Create Token
  ´´´
  copy the token.

  In jenkins paste it to "Your github access token" -place and click:
  ´´´
  Connect
  ´´´


### Choose your GitHub-account ###

Now choose your python repo
```
Create pipeline
```

----------------------------------------
### Editing pipeline ###

![default](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor01.png)

Click to "Any"

Change it to: Docker

Add image as: python:3

![Docker with python:3](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor02.png)

Click the plus-button ![plus-button](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor03.png) to add a stage ![larger-plus-button](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor04.png)

Name it to Build as seen on picture
![build](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor05.png)

Click: ```Add step```

and choose:
```
Shell Script
```
![Shell Script](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor05.png)

Add this line to the script:
```
python *.py
```

![sh](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor07.png)

Click: ``` Save ``` ![Save](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor08.png)

And finally click: ``` Save & Run ```
![Done](https://github.com/lnxbusdrvr/mddocs/blob/master/jknsBOceanPipelineEditor09.png)




