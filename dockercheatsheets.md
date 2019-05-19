# The Ultimate Docker Cheatsheets

### Full Cheatsheets

![The full cheatsheets](/images/dockercheatsheet8.png)

### Container management commands

![Container management](/images/dockercheatsheet1.png)

### Inspecting the container

![Inspecting the container](/images/dockercheatsheet3.png)

### Interacting with the container

![Interacting with the container](/images/dockercheatsheet4.png)

### Image management commands

![Image management commands](/images/dockercheatsheet5.png)

### Image transfer commands

![Image transfer commands](/images/dockercheatsheet6.png)

### Builder main commands

![Builder main commands](/images/dockercheatsheet7.png)

## Docker cli

## Dockerfile

inheritance

```vim
from ruby:2.2.2
```

variables

```vim
env app_home /myapp
run mkdir $app_home
```

initialization

```vim
run bundle install
```

```vim
workdir /myapp
```

```vim
volume ["/data"]
# specification for mount point
```

```vim
add file.xyz /file.xyz
copy --chown=user:group host_file.xyz /path/container_file.xyz
```

onbuild

```vim
onbuild run bundle install
# when used with another file
```

commands

```vim
expose 5900
cmd ["bundle","exec","rails","server"]
```

entrypoint

```vim
entrypoint ["executable","param1","param2"]
entrypoint command param1 param2
```

configures a container that will run as an executable

```vim
entrypoint exec top -b
```

this will use shell processing to subtitute shell variables, and will ignore any cmd or docker run command line arguments

## metadata

```vim
label versio="1.0"
```

```vim
label "com.example.vendor"="acme incorporated"
label com.example.label-with-value="foo"
```

```vim
label description="this text illustrates \
that label-values can span multiple lines."
```

## docker-compose

### basic example

```yml
version: '2'

services:
  web:
    build: .
    # build from dockerfile
    context: ./path
    dockerfile: dockerfile
    ports:
     - "5000:5000
    volumes:
     - .:/code
  redis:
    image: redis
```

### commands

```vim
docker-compose start
docker-compose sstop
```

```vim
docker-compose pause
docker-compose unpause
```

```vim
docker-compose ps
docker-compose up
docker-compose down
```

### building

```yml
web:
  #build from dockerfile
  build: .
```

```yml
#build from custom dockerfile
build:
  context: ./dir
  dockerfile: dockerfile.dev
```

```yml
  image: ubuntu
  image: ubuntu:14.04
  image: tutum/infuxdb
  image: example-registry:4000/postgresql
  image: a4bc65fd
```

### ports

```yml
ports:
  - '3000'
  - '8000:80' #guest:host
```

```yml
# expose ports to linked services (not to host)
expose: ['3000']
```

### commands

```yml
  # command to execute
  command: bundle exec thin -p 3000
  command: [bundle, exec, thin, -p, 3000]
```

```yml
  # override the entrypoint
  entrypoint: /app/start.sh
  entrypoint: [php, -d, vendor/bin/phpunit]
```

### environment variables

```yml
  # environment vars
  environment:
    rack env: development
  environment:
    - rack_env=development
```

```yml
  # environment vars from file
  env_file: .env
  env_file: [.env, .development.env]
```

### dependencies

```yml
# makes the `db` service available as the hostname `database`
# (implies depends_on)
links:
  - db:database
  - redis
```

```yml
# make sure `db` is alive before starting
depends_on:
  - db
```

### other options

```yml
## make this service extend another
extends:
  file: common.yml #optional
  service: webapp
```

```yml
volumes:
  - /var/lib/mysql
  - ./_data:/var/lib/mysql
```

### labels

```yml
services:
  web:
    labels:
      com.example.description: 'accounting web app'
```

### dns servers

```yml
  services:
   web:
    dns: 8.8.8.8
    dns:
     - 8.8.8.8
     - 8.8.4.4
```

### devices

```yml
services:
  web:
    devices:
      - '/dev/ttyusb0:/dev/ttyusb0'
```

### external links

```yml
services:
  web:
    external links:
      - redis 1
      - project_db_1:mysql
```

### hosts

```yml
services:
  web:
    extra hosts:
      - 'somehost:192.168.1.100'
```
