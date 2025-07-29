# Docker Command Line Interface Tutorial

docker images # lists all docker images  
docker ps # lists all running containers # add -a tag to list all running and tsopped ocntainers  
  
### Pulling an Image (from Docker Hub or wherever)  
```
docker pull {imagename}:{tag} # where name is name of image, and tag is version of image
```
  
### Running an Image  
This image does not necessarily have to be already present in our docker, as then this command will automatically pull the image for us.  
```
docker run --name {name_of_container_to_be_created} -d -p 8080:80 {imagename}:{tag}
# where -p maps port 8080 in localhost to port 80 inside the container (Concept of Port Binding). Localhost port can be randoma s long as it isn't in use, but container ports are usually specific. Just search for the default port of a specific container only. (ex. what is the default port for mySQL?)
# where -d detachs the docker process logs from terminal (making the terminal cleaner)
# --name to name the container we are creating by running our image
```

### Running a Container  
```
docker run {name_of_container} {any_additional_command_line_commands_the_container_expects}
```
### Building an Image from a Dockerfile
```
docker build -t {name_of_image_to_be_created} {location_of_docker_file}
```

### Starting and Stopping a Container
```
docker start {containername/containerid}
docker stop {containername/containerid}
```

### Renaming an Image  
```
docker tag {name_of_image} {your_username}/{name_of_new_image}
```
