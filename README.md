# D17A_Group2_LoadBalancingUsingDocker-

ABSTRACT:
Our aim is to set up an installation that has Haproxy server at the front end and a set of upstream servers handling the requests.The haproxy server is the only directly communicating with clients.Clients don’t receive any information about particular server handling their request .The responses appear to come directly from the proxy server .All the incoming requests are distributed among all the available containers resulting in equal data usage among all.

INTRODUCTION:

Let’s imagine that we plan to deploy an application that is expected to be heavily used. The assumption is that a single server can’t handle all incoming requests. We need multiple instances. Therefore the server instance can’t meet expected performance requirements. Or we simply want to deploy web application across multiple instances to ensure that if one instance fails,we still have another instance operating.

Docker allows us to easily and efficiently run multiple instances of the same service. Docker
containers are designed to be able to build up a container very quickly on the VM regardless the underlying layers
.
Nevertheless, such installation allows us to run multiple containers as separate objects. When
building such infrastructure, it is desirable to keep all the instances available over one URL. The
requirement can be satisfied by the usage of the load balancer node.

Our aim is to set up an installation that has an Nginx proxy server at the front and a set of
upstream servers handling the requests. The Haproxy server is the one directly communicating with clients. Clients don’t receive any information about particular upstream server handling their
requests. The responses appear to come directly from the proxy server.

Implementation:

DOCKER:
Docker is a computer program that performs operating-system-level virtualization also known as containerization. It is developed by Docker, Inc Docker is primarily developed for Linux, where it uses the resource isolation features of the Linux kernel such as cgroups and kernel namespaces, and a union-capable file system such as OverlayFS and others[8] to allow independent "containers" to run within a single Linux instance, avoiding the overhead of starting and maintaining virtual machines (VMs). 

The steps for installation are:

Update the apt package index.
1. $ sudo apt-get update
2. Install the latest version of Docker, or go to the next step to install a specific version. Any
existing installation of Docker is replaced.
3. Use this command to install the latest version of Docker:

The contents of the list depend upon which repositories are enabled, and will be specific to your
version of Ubuntu (indicated by the xenial suffix on the version, in this example). Choose a
specific version to install. The second column is the version string. The third column is the
repository name, which indicates which repository the package is from and by extension its
stability level. To install a specific version, append the version string to the package name and
separate them by an equals sign (=):

4. $ sudo apt-get install docker-ce=<VERSION>
5. Verify that Docker CE or Docker EE is installed correctly by running the hello-world image.
    $ sudo docker run hello-world.

HAProxy:
HAProxy, which stands for High Availability Proxy, is a popular open source software TCP/HTTP Load Balancer and proxying solution which can be run on Linux, Solaris, and FreeBSD. Its most common use is to improve the performance and reliability of a server environment by distributing the workload across multiple servers (e.g. web, application, database). It is used in many high-profile environments, including: GitHub, Imgur, Instagram, and Twitter.

BACKEND
A backend is a set of servers that receives forwarded requests. Backends are defined in the backend section of the HAProxy configuration. In its most basic form, a backend can be defined by:
1.which load balance algorithm to use
2.a list of servers and ports
A backend can contain one or many servers in it--generally speaking, adding more servers to your backend will increase your potential load capacity by spreading the load over multiple servers. Increase reliability is also achieved through this manner, in case some of your backend servers become unavailable.
Here is an example of a backend configuration, web-backend and blog-backend with two web servers in each, listening on port 80:

backend web-backend
  balance roundrobin
  server web1 web1.yourdomain.com:80 check
   server web2 web2.yourdomain.com:80 check
Steps for installing HAProxy:
To install HAProxy from an outside repo, you will need to add the new repository with the following command.
            sudo add-apt-repository ppa:vbernat/haproxy-1.
      2.  update your sources list
            sudo apt update.
       3.  Install HAProxy 
           sudo apt install -y haproxy


CONCLUSION:

HAProxy is an efficient way to perform load balancing in order to provide fail-over, increase the
availability, extend fleet of the application servers, or to unify the access point to the installation.
Docker containers allow quickly spawn multiple instances of the same type on various nodes.
Combined together, it is an easy and powerful mechanism for solving similar challenges.


REFERENCES:

1. Web article on “How to run a load balance service in docker containers”,
    http://www.openstack.org

2. Docker Documentation - ‘Docker Cloud: Create a proxy and load balancer’,
   “http://docs.docker.com”

3. HAProxy Load Balancing tutorial, “https://www.upcloud.com”
    







