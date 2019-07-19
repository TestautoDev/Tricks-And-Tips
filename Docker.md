https://qxf2.com/blog/view-docker-container-display-using-vnc-viewer/

http://realestate-com-au.github.io/intro-to-docker/#1

### Docker login to container
``
docker exec -it <mycontainer> bash    
``
### Docker login to image
``
docker run -it <image> bash  
``
### Docker login to image with entry point
``
docker run -it --entrypoint bash <image>
``
### Docker conatainer run with priviledge
--privileged
  
### Docker containers:
docker ls
docker ps

### Docker images:
docker images
