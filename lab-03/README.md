# Lab 03 - Basic Docker commands

To introduce you to the world of docker we will list some of the basic commands.
These are the commands you are probably going to use the most.

This lab is created to show you the basic Docker commands. In this lab you will
see some output for most of the commands but be aware that this probably won't be
the case if you do them on your `clean` docker host. 

## Task 1: Docker info


        docker info


The above command should generate output such as the output below:


        Containers: 7
         Running: 0
         Paused: 0
         Stopped: 7
        Images: 7
        Server Version: 18.09.2
        Storage Driver: overlay2
         Backing Filesystem: extfs
         Supports d_type: true
         Native Overlay Diff: true
        Logging Driver: json-file
        Cgroup Driver: cgroupfs
        Plugins:
         Volume: local
         Network: bridge host ipvlan macvlan null overlay
         Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
        Swarm: inactive
        Runtimes: runc
        Default Runtime: runc
        Init Binary: docker-init
        containerd version: 9754871865f7fe2f4e74d43e2fc7ccd237edcbce
        runc version: 09c8266bf2fcf9519a651b04ae54c967b9ab86ec
        init version: fec3683
        Security Options:
         seccomp
          Profile: default
        Kernel Version: 4.9.125-linuxkit
        Operating System: Docker for Mac
        OSType: linux
        Architecture: x86_64
        CPUs: 2
        Total Memory: 1.952GiB
        Name: linuxkit-025000000001
        ID: 5GMH:JGA5:NRE7:453Z:DOBB:KFGU:VV7E:O2EF:57AS:WUWX:5HZK:HMNF
        Docker Root Dir: /var/lib/docker
        Debug Mode (client): false
        Debug Mode (server): true
         File Descriptors: 24
         Goroutines: 51
         System Time: 2019-02-27T10:55:52.3772358Z
         EventsListeners: 2
        HTTP Proxy: gateway.docker.internal:3128
        HTTPS Proxy: gateway.docker.internal:3129
        Registry: https://index.docker.io/v1/
        Labels:
        Experimental: true
        Insecure Registries:
         127.0.0.0/8
        Live Restore Enabled: false
        Product License: Community Engine

## Task 2: Pull an image

Public images on `Dockerhub` can be pulled or "downloaded" to your own sytem.
This is simply done with the `docker pull` command.

        docker pull nginx

        Using default tag: latest
        latest: Pulling from library/nginx
        743f2d6c1f65: Pull complete
        6bfc4ec4420a: Pull complete
        688a776db95f: Pull complete
        Digest: sha256:23b4dcdf0d34d4a129755fc6f52e1c6e23bb34ea011b315d87e193033bcd1b68
        Status: Downloaded newer image for nginx:latest

This `docker pull` command will pull the `latest` version of nginx. You are also
able to define a specific tag in this command. When you do this you will pull or
"download" a specific version of the image.

        docker pull nginx:stable-alpine-perl

        stable-alpine-perl: Pulling from library/nginx
        e7c96db7181b: Pull complete
        b222e56557a3: Pull complete
        Digest: sha256:c0f8551b10f8bea71fb6406c50365c9fa42052acb4fca1ca4eeaa148f6fb6e68
        Status: Downloaded newer image for nginx:stable-alpine-perl


## Task 2: List the containers

To see what containers are running at the moment you can use the `ps` commando.

        docker ps

        CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
        d6fc46ec3f49        nginx               "nginx -g 'daemon of…"   47 seconds ago      Up 46 seconds       0.0.0.0:8080->80/tcp   recursing_ganguly

The basic `docker ps` command will only list running containers. If you want to
see all containers that are on the system you can use the `-a` option.

        docker ps -a

        CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                      PORTS                  NAMES
        729890d7978a        nginx               "nginx -g 'daemon of…"   40 seconds ago       Exited (0) 27 seconds ago                          boring_darwin
        d6fc46ec3f49        nginx               "nginx -g 'daemon of…"   About a minute ago   Up About a minute           0.0.0.0:8080->80/tcp   recursing_ganguly

## Task 3: List the images

To see what images are on the system you can use this commando:

        docker images

        REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
        alpine              latest              055936d39205        2 weeks ago         5.53MB
        nginx               stable-alpine-perl  dfe32420dd8c        2 weeks ago         54.7MB
        nginx               latest              53f3fd8007f7        2 weeks ago         109MB
        centos              latest              9f38484d220f        2 months ago        202MB

This will list all the images that are currently downloaded to the system.

## Task 4: Delete containers or images

To delete certain things you can use the `rm` commando. For containers this would
be:

         docker rm <container_id>

         729890d7978a

Delete the first nginx container shown in the command above. Given that this is the
container you would need to delete you would have to use the id `729890d7978a`.
The output for the `rm` command is just the `ID` of the container.

For images:

         docker image rm <image_id>

         Untagged: alpine:latest
         Untagged: alpine@sha256:769fddc7cc2f0a1c35abb2f91432e8beecf83916c421420e6a6da9f8975464b6
         Deleted: sha256:055936d3920576da37aa9bc460d70c5f212028bda1c08c0879aedf03d7a66ea1
         Deleted: sha256:f1b5933fe4b5f49bbe8258745cf396afe07e625bdab3168e364daf7c956b6b81

Here the `alpine` image is deleted from the system.

The `ID's` of the containers and images are found with the commands you found in
`Task 1` and `Task 2`.
