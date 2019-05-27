# Lab 02 - Install Docker on the cloud instance

In the previous lab we connected to the cloud instance we provided. The goal
of this lab is to install `Docker` on this instance.

## Task 1: Install Docker

Fortunatly for us there is a one line command to install `Docker` on this instance.

        curl -sSL https://get.docker.com/ | sh

When this script is finished we should have `Docker` installed on the instance.
Verify with the following command :

        docker --version

If `Docker` is correctly installed you should get something like this :

        Docker version 18.09.6, build 481bc77

## Task 2: Add ubuntu user to the Docker group

This is a step you don't really have to remember from this workshop but it's a
lot easier for the following labs if we put your user in the `Docker group`. This
is the group that can access the `Docker` service without using `sudo`.

        sudo usermod -aG docker ubuntu

Since we've brought it up, this command will modify the user ubuntu and `-a (append)`
`-G (groups)` the `docker` group to the ubuntu user. If we used `-g` the command
you wil overwrite your primary group. Most of the time this is not what we want. 

Before we can use this new group we need to logout and log back in via ssh.

Congratulations, you have now completed this lab.
