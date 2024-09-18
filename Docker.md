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
```dockerfile
FROM debian:bullseye-20240211 // image distro and colon (image tag)

WORKDIR /usr/src // <- put source code here

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

#### Build
`docker build . -t tagname`
Add files to `.dockerignore` like git

- Docker desktop
- Docker scout
#### Run
`docker run progname`
`docker ps` - running and stopped containers
`docker stop` or `docker kill`
`docker push` - to a remote registry
`docker pull ...`

### Testing
`docker pull [debian]`
`docker images` - check which images are installed
`docker create debian` why random name
`docker start [name of container]`
`docker exec -it [container] zsh`

#### References

[[Virtual Machine]]

_2024-05-25 10:50_