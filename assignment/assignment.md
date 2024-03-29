# Deploying a Flask application on AWS using Docker

## Creating Docker Images
There is a simple Flask web application utilizing a Bootstrap template in the
`web_app` folder.  It used the Stater Template.  You can use this one, or use a different one
(e.g. the Jumbotron).  Your assignment is to use Docker to deploy this application
first locally on your laptop and then secondly on AWS.

0. Verify that you can run the Flask app locally. Note which port it's using to connect to the client.   
   ```
   $ python app.py
   ```

#### Create a Docker Image

1.  Create a `Dockerfile`.  It's just a text file with no extension.  Use the Dockerfile [example](https://docs.docker.com/get-started/part2/#define-a-container-with-dockerfile)
   as a guide.  Some tips:  
   - You probably don't want `python:2.7-slim`  Look at what python tags are available on [Docker Hub.](https://hub.docker.com/_/python/)  
   - Be sure to expose the port that the Flask app uses (it's not 80 as in the example).  
   - You don't need the environment variable.  

2. Create a `requirements.txt` file.  
   - You don't need Redis, but you will need Flask.
    
3. Put the `Dockerfile` and `requirements.txt` in the same directory as your `app.py`.  
   Then [build the Docker Image from the Dockerfile.](https://docs.docker.com/get-started/part2/#build-the-app)

4. Create and run your container using `docker run`
   - You should be able to go to the port you mapped the container port to in the browser and see the app.

### Push your Image up to Docker Hub
6. [Tag](https://docs.docker.com/get-started/part2/#tag-the-image) and [Publish](https://docs.docker.com/get-started/part2/#publish-the-image)
   your image.

### Test your remote image locally

7. [Pull and run your image locally.](https://docs.docker.com/get-started/part2/#pull-and-run-the-image-from-the-remote-repository)


### Install Docker on AWS


8. [Follow this guide to install Docker on an Amazon Linux instance.](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html?shortFooter=true#install_docker)
   - In security settings, be sure to add a Custom TCP rule where you allow communication on the port that you specified in the Dockerfile.
   A simple way to keep things straight is to use the same port in the Flask app, in the Dockerfile, in the AWS security settings, and to
   map that port to the AWS port when you run the container.

### Create a Docker Container on AWS

9. Use `docker run` to pull down your image and make a container.  You should be able to go to the ec2 address:port in your browser and see your app running!
