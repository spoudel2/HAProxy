
# HAProxy

HAProxy is a free, very fast and reliable solution offering high availability, load balancing, and proxying for TCP and HTTP-based applications. It is particularly suited for very high traffic web sites and powers quite a number of the world's most visited ones. Over the years it has become the de-facto standard opensource load balancer, is now shipped with most mainstream Linux distributions, and is often deployed by default in cloud platforms. Since it does not advertise itself, we only know it's used when the admins report it :-)

Its mode of operation makes its integration into existing architectures very easy and riskless, while still offering the possibility not to expose fragile web servers to the internet.

This role install HAProxy to remote hosts, configure and make environment fully up.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development, testing purposes and even for production. See deployment for notes on how to deploy the project on a live system.

### Asumption of this project.

1. You must assign your remote HAProxy URL/DNS to `hosts` file. For demo I have used localhost(127.0.0.1)
2. In roles/haproxy/vars/main.yml you have to define your upstream server and the port where your application is listening. For this demo I have used 7 localhost instances with the the same port.


### Installing
```
yum install -y epel-release git ansible
```

### Deployment

```
git clone https://github.com/poudelpra/HAproxy.git
cd HAproxy
ansible-playbook haproxy.yml
```
