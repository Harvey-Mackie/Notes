# Core Features
### **Image**
A lightweight, standalone software package containing code, runtime, and dependencies, such as `mysql:latest`.

### **Container** 
An active runtime instance of an image, like a running MySQL database within a Docker container.
### **Volume**
A persistent storage mechanism enabling data sharing between containers and the host, e.g., mounting `/var/lib/mysql` from the host to `/var/lib/mysql` in the container, ensuring database data persists even if the container is removed.

## Docker Compose
A tool for defining and running multi-container Docker applications using a YAML file, specifying configurations and dependencies, such as a MySQL database service and a backend API service.
```yaml
version: '3.8'

services:
  api:
	image: my-api-image:latest
	ports:
	  - "8080:8080"
	volumes:
	  - ./api:/app  # Mount local directory 'api' into container's '/app' directory
	depends_on:
	  - database

  database:
	image: mysql:5.7
	environment:
	  MYSQL_ROOT_PASSWORD: example
	  MYSQL_DATABASE: mydatabase
	ports:
	  - "3306:3306"
	volumes:
	  - ./database:/var/lib/mysql  # Mount local directory 'database' into container's MySQL data directory
```


