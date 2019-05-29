# Lab 01 - Connect to the cloud instance

The first thing we are going to do is run `Docker` in the cloud. We provided a
cloud instance for each student and will share the needed files to connect to
this instance.

## Task 1: Install Putty

To connect to this cloud instance we will need `Putty`. You can download it
[here](https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.71-installer.msi).

Fill in the `hostname or ip address` box with the provided `ip address` this
is going to be `instance<number>.gluo.cloud`. Port
`22` is already the correct port. This doesn't need any other configuration.

The `.ppk` file that is needed for the next configuration is going to be provided
by us via Slack.

We will have to do some more configuration to connect to the instance though. Go
to `connection -> ssh -> auth -> private key file for authentication` select the
`.ppk` file provided by Gluo. Afterwards be sure to specify the username, this is
done in `connection -> data -> auto-login username` the value of this box should
be `ubuntu`.

Click `open` and you should be connected to the instance.

## Task 2: Initial commands

Before you are able to install some packages you will need in the next labs you
will have to update your `cloud instance`. This is not really a docker workshop
scope but it's nice to know anyway.

        sudo apt update
