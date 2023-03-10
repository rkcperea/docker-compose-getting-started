###### copied at Time.at(1678460340) src: https://docs.docker.com/compose/gettingstarted/

# Try Docker Compose 
Important
```
From the end of June 2023 Compose V1 won’t be supported anymore and will be removed from all Docker Desktop versions.
```

Make sure you switch to Compose V2 with the docker compose CLI plugin or by activating the Use Docker Compose V2 setting in Docker Desktop. For more information, see the Evolution of Compose

This tutorial is designed to introduce the key concepts of Docker Compose whilst building a simple Python web application. The application uses the Flask framework and maintains a hit counter in Redis.

The concepts demonstrated here should be understandable even if you’re not familiar with Python.

Prerequisites
You need to have Docker Engine and Docker Compose on your machine. You can either:

Install Docker Engine and Docker Compose as standalone binaries
Install Docker Desktop which includes both Docker Engine and Docker Compose
You don’t need to install Python or Redis, as both are provided by Docker images.

(proceed to [composetest](composetest))
 