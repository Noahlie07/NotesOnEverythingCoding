# Dockerfile

### What is a dockerfile for?
A dockerfile is a script of instructions for building a docker image out of our application. It is the script that "dockerizes" our application.  

### Structure of Dockerfile and Dockerfile Directives
Dockerfiles start with a parent image/base image. We choose the base image we need, depending on which tools our application uses (ex. python image).  

**Dockerfile Directives - FROM**
```
FROM python:latest
# when application is run, it will have access to python as it pulls from a python image.
# This python image can be said is a base image.
```
**Dockerfile Directives - RUN**  
Run's command line commands in the container. Useful for downloading libraries.  
```
RUN pip install docling
```

**Dockerfile Directives - COPY**  
Copy application files/directories from our local computer and paste them into the container
```
COPY {path_of_file/directory_in_our_computer} {path_of_file_we_will_paste_to_in_the_container}
```

**Dockerfile Directives - WORKDIR**  
Sets the working directory in the container for all following commands
```
WORKDIR {path_of_dir}
```

**Dockerfile Directives - CMD**  
Runs the last command line command in the container. As the last command, there can only be one CMD in a container.
```
CMD ["{command}", "{parameter}"]
```
