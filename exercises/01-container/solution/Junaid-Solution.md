Used these commands , 

1. First cloned into my local machine using these commands 
  * git init
  * git clone https://github.com/bmuschko/ckad-crash-course/tree/master/exercises/01-container/app

2. Verified the code in my pc

3. To move this code to my personal repo, i used these commands
     *git config --global user.email "mohammadjunaidofficial@gmail.com"
     *git config --global user.name "Junaid"
     *git remote add origin https://github.com/mohammadjunaidm/Acabes-Devops-Learning.git
     *git remote -v (to verify the repo is set into my personl account)
     *git add .
     *git commit -m "Test"
     *git push -u origin main

4. Verified the code in my personal repo

5. Used docker login to authenticate myself

6. Used this
      docker build -t junaid-hello-project .

7. Verified using docker images command using docker images

8. Used this 
     docker tag junaid-hello-project junaid1998/junaid-hello-project:latest

9. Used this
     docker push junaid1998/junaid-hello-project:latest (To push it into my dockerhub account)

10. Run the container using 

    docker run -d -p 3000:3000 --name hello-app junaid1998/junaid-hello-project:latest

11. Verified the app is running in browser on port 3000

12. Verified the logs using the below command

docker logs 0bdb59ac713e
Magic happens on port 3000

13. Created .tar file and moved the image into it

    docker save -o junaid-hello-project.tar junaid1998/junaid-hello-project:latest
 
