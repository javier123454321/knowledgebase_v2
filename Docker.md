- Development often breaks when you change the working environment.
- Microservices

    - Applications that run independently of each other. (Small processes that communicate over a network)

They often dont use the full capacity of the [[virtual machine]] that it is hosted on.


        - Advantages:
- applications can be easier to maintain if split up
- updating a particular software or stack on one service is easier
- Any services can go down independently


        - Problems
- If you have a host machine and VM, the VM will be consuming a lot of unused ram
- If there are multiple (dozens) of microservices, VMs don't make sense.


    - ### Docker works like this
        - Host > [[virtual machine]] > Multiple Docker Containers

        - Docker Containers use the necessary memory to run their programs.

        - Provides a consistent computing environment.
        - Docker does not use the guest OS, but the host.
        - Host > Docker Engine - Container 1 with Binaries
		\
		Container 2 with Binaries

- Docker Images
A read only template used to create containers
Contains all the dependencies for a microservice - can be created or pulled
- Containers 
The runtime of docker images.
