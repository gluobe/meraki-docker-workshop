# Lab 03 - Basic Docker commands

To introduce you to the world of docker we will list some of the basic commands.
These are the commands you are probably going to use the most.

## Task 1: Docker info


        sudo docker info


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


## Task 2: List the containers

To see what containers are running at the moment you can use the `ps` commando.

        sudo docker ps

The basic `docker ps` command will only list running containers. If you want to
see all containers that are on the system you can use the `-a` option.

        sudo docker ps -a

## Task 3: List the images

To see what images are on the system you can use this commando:

        sudo docker images

This will list all the images that are currently downloaded to the system.

## Task 4: Delete containers or images

To delete certain things you can use the `rm` commando. For containers this would
be:

        sudo docker rm <container_id>

For images:

        sudo docker image rm <image_id>

The `id's` of the containers and images are found with the commands you found in
`Task 1` and `Task 2`.
