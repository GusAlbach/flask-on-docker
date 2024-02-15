## Overview

This repo utilises Flask, Docker, Postgres, Gunicorn, and Nginx to loosely imitate the tech stack of instagram. Utilising this tech stack, this repo can support the uploading of a file to a server, and the remote access of that file (an image). Done through a web browser, this works similar to a stripped down social media app. Docker's general purpose is to standardize software versions / downloads across users so that the same programs can run successfully on different systems. As a result, this product should be able to work across different systems and computers. Below is a gif of an image being uploaded and then being served through a seperate link. My apologies as the gif only illustrates that the photo was uploaded, but does not show the full screen. 

<img width=600px src=big_data_gif.gif /></a>

## Build Instructions
In order to run this, one first must build and spin up the docker containers associated with the project. Once these are built, the project can then be viewed through a web browser. 

```
docker-compose -f docker-compose.prod.yml up -d --build
```
This command builds and spins the initial web servers. The `-d` ensures that they will run in the background as a "daemond", meaning you can continue to write commands in the terminal without interrupting the process.
```
docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
```
This docker-compose command creates the database to store all information iuploaded to the web servers. 

### Uploading images
In my experience, I had to utilise port forwarding to access the web server, but you likely will not need to. As such, an image cna be uploaded at the url http://localhost:7340/upload . By then loading http://localhost:7340/media/IMAGE-NAME , this picture can be viewed. Keep in mind that "IMAGE-NAME" should be replaced with the name of the image you uploaded. You now shouldhave everything up and running!
