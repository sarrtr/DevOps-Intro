# Lab 6 submission

## Task 1

![6.1](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.1.jpg?raw=true)
![6.2](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.2.jpg?raw=true)
![6.5](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.5.jpg?raw=true)

- Image size: 119MB
- Layer count: 1
- Tar file size: 30.2MB

Tar file size is less than full image size (image layers are compressed) and roughly equal to content size of image. Tar file contains layer data and metadata, manifest file, config file and repository information.

![6.3](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.3.jpg?raw=true)
![6.4](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.4.jpg?raw=true)

Image removal fails when a container exists because image is the base for container and it keeps base file system for its container. When we try to remove image with existing containers we try to break their integrity: the container will have nothing to rely on.

## Task 2

![6.6](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.6.jpg?raw=true)
![6.7](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.7.jpg?raw=true)
![6.8](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.8.jpg?raw=true)
![6.9](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.9.jpg?raw=true)

- `diff` output: 
`C` indicates that these files or directories were changed after the container started. Specifically, Nginx created a runtime process ID file (/run/nginx.pid) and modified its default configuration file (/etc/nginx/conf.d/default.conf).

- Advantages and disadvantages of `docker commit` vs Dockerfile for image creation:
    - `docker commit` is quick and easy for testing/debugging, there is no need to write configuration files. But at the same time it captures runtime artifacts (like PID files) and produces larger image sizes due to unnecessary files, also it is not reproducible or version controllable.
    - Dockerfile is fully reproducible and automatable, it produces smaller, optimized images, also it is easy to modify and extend it. But it requires more initial setup and we must manually specify all changes.

## Task 3

![6.10](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.10.jpg?raw=true)
![6.11](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.11.jpg?raw=true)

Docker has an embedded DNS server that automatically resolves container names to IP addresses when containers are on the same user-defined network, allowing communication via container name instead of IP.

User-defined bridge advantages:
- Automatic DNS resolution between containers
- Better isolation
- Ability to attach/detach containers dynamically

## Task 4

![6.12](https://github.com/sarrtr/DevOps-Intro/blob/main/labs/assets/screenshots/lab6.12.jpg?raw=true)

Why persistence matters:
Persistence ensures data survives container restarts, updates, or crashes, which is critical for databases, user uploads, and application state.

Volumes vs bind mounts vs container storage:
- Volumes: Managed by Docker. Use for: Production data, databases, backups—best performance, portable, Docker-managed.
- Bind mounts: Map host directory into container. Use for: Development, configuration files, sharing host data.
- Container storage (ephemeral): Inside container's writable layer. Use for: Temporary files, cache, anything non-critical—data dies with container.
