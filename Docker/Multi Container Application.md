# Multi Container Application (MCA)
Multi container applications are containers that contain containers inside them. Each of these containers inside them are called a service.  
Containers within a multi-container application can communicate with each other through a shared network, allowing services to interact.  

## Docker Compose  
Docker Compose is the primary tool for defining and running multi-container Docker applications.  
It utilizes a YAML file (typically docker-compose.yaml or compose.yaml) to configure the application's services, networks, volumes, and other settings.  

A single docker-compose.yaml file centralizes the configuration and allows for starting, stopping, and managing the entire application with a single command.  
This single command is **docker-compose up -d**, to be run in the command line in the directory of the MCA.
