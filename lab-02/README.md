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

You have now completed this lab.
