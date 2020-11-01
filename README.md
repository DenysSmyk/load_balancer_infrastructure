# Load balancer infrastructure
##### Load balancer nginx (round-robin) and two endpoints (flask), provision by Ansible.

Load balancing across multiple application instances is a commonly used technique for optimizing resource utilization, maximizing throughput, reducing latency, and ensuring fault-tolerant configurations.

It is possible to use nginx as a very efficient HTTP load balancer to distribute traffic to several application servers and to improve performance, scalability and reliability of web applications with nginx.

In this project, the method of load balancing is a round-robin - requests to the application servers are distributed in a round-robin fashion.

This project is built on three vagrant virtual machines(hashicorp/bionic64):
1. Nginx 192.168.50.3
2. Web 1 192.168.50.4
3. Web 2 192.168.50.5

### Structure
![](img/lb.png)

### Requirements
* Vagrant
* Ansible

### Installation
`$ git init`

`$ git clone https://github.com/DenysSmyk/load_balancer_infrastructure`

`$ vagrant up --provision`

After the vagrant service is running, it will be available on  http://192.168.50.3

![](img/lb_web1.png) ![](img/lb_web2.png)
