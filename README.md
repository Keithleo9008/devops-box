# DevOps box

A vagrant project with an ubuntu box with the tools needed to do DevOps.

# Tools included

* Docker
* Terraform
* Packer
* AWS CLI
* Ansible

# Synced folders

Per the Vagrantfile, the parent folder of this Vagrantfile's folder
will be synced to the "/projects" directory in the Vagrant box.  You
can create Dockerfiles in sibling directories, and then build Docker
images in the VM.

## A sample Docker project

e.g., with the below directory layout:

    /<parent>
      /<this_directory>
         Vagrantfile

cd to the /parent directory and clone the sample project
https://github.com/jeff-zohrab/docker_static_site, and build that
project's Dockerfile:

    # On your machine (the host)
    cd /parent/<this_directory>
    vagrant up
    vagrant ssh

    # Now in the vagrant box:
    cd /projects
    ls
    cd /docker_static_site
    docker build -t webserver-image:v1 .
    # See the docker_static_site README for more.

If you run the docker_static_site's resulting Docker image, you'll be
able to see it from your machine at 192.168.199.9, part of a private
network created in the Vagrantfile.
