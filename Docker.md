#todo #Programming 
#### Vertical Scaling
Increase the capacity of your current server, RAM & CPU but a ceiling will be reached.
#### Horizontal Scaling
Distribute code to multiple smaller services
#### Hypervisor / Virtual Machines
Isolates and runs multiple operating systems on a machine.
### Docker / Container-Based
Docker have minimal footprints as they package only the app and its dependencies.
- Dockerfile - a blueprint that tells Docker how to configure the environment
- Dockerfile is used to build an image which contains an OS, dependencies and code
- Image must be run as a container
- Containers are stateless: when shutdown all data within them is lost. Makes them portable
#### Dockerfile
A text file that contains commands used to build a docker image
```dockerfile
FROM debian:bullseye-20240211 // image distro and colon (image tag)

# creates a folder in the container's file system
WORKDIR /usr/src // <- put source code here

# anything run after WORKDIR takes place in WORKDIR
RUN apt-get update && \ // runs any command like in the shell
	apt-get install -y python3 python3-pip // install dependencies

RUN useradd --create-home appuser // nonroot user for security
USER appuser
COPY app.py . // copy local code to image

ENV API_KEY=hi_mom // environment variable

EXPOSE 8000 // to make a port accessible

CMD [ "python3", "-m", "http.server", "8000" ] // command (can be only one)

ENTRYPOINT [ "python3", "-m", "http.server" ] // allows you to pass arguments to the command when run
CMD ["8000"]

LABEL maintainer="Tim Hopgood" // for metadata (version, description)

// healthcheck to ensure it's running properly
HEALTHCHECK --interval=30s --timeout=10s \
	CMD curl -f http://localhost:6969/health || exit 1

VOLUME /db/data // mount volume if it needs to store data
```
#### Docker Compose
A tool for defining and running multi-container  applications. It allows you to define a set of containers and their dependencies in a single file `docker-compose.yml`.

#### Build
`docker build . -t tagname`
Add files to `.dockerignore` like git

- Docker desktop
- Docker scout
#### Run
`docker run progname`
`docker ps` - running and stopped containers (process status)
`docker ps -a` - all containers
`docker stop` or `docker kill`
`docker push` - to a remote registry
`docker pull ...`
### Testing
`docker pull [debian]`
`docker images` - check which images are installed
`docker create -it --name some_name debian(image_name) [cmd]` - creates container
`docker run some_name` runs container
You can instead use:  
`docker run -it --name some_name debian` - to create and run in one command (`-it` interactive mode/pseudo TTY)
`docker start -ai [name of container]`
`docker exec -it [container] [/bin/bash OR zsh]` - executes `bash` or `zsh` in container to access the cli
*OR*
`docker attach [container id]` - attaches your terminal to CLI of container
`docker run --name container_name -v /local/path:/container/path -it my-image` - mounts local path to container path 

`docker inspect {image}` - shows architecture etc for image

#### References

[[Virtual Machine]]

_2024-05-25 10:50_