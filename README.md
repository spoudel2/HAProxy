HAProxy is a free, very fast and reliable solution offering high availability, load balancing, and proxying for TCP and HTTP-based applications. It is particularly suited for very high traffic web sites and powers quite a number of the world's most visited ones. Over the years it has become the de-facto standard opensource load balancer, is now shipped with most mainstream Linux distributions, and is often deployed by default in cloud platforms. Since it does not advertise itself, we only know it's used when the admins report it :-)

Its mode of operation makes its integration into existing architectures very easy and riskless, while still offering the possibility not to expose fragile web servers to the internet.

This ansible role install HAProxy to remote hosts, configure and make environment read.

Asumption of this project.

1. You must assign your remote HAProxy URL/DNS to `hosts` file. For demo I have used localhost(127.0.0.1)
2. In roles/haproxy/vars/main.yml you have to define your upstream server and the port where your application is listening. For this demo I have used 7 localhost instances with the the same port.


Aslo, this role has capability to work upto 10 upstream servers, if you need more please edit haproxy.cfg.j2. I beleive 10 HAProxy instances are more then enough to handle your circumstances. Most of the production environmant use few HAProxy instances. 
If you are intended to used less then 10 HAP instances, you can leave haproxy.cfg.j2 as it is because the script is smart enough to check your variables defined vars/main.yml and limit the output by only the defined servers, i.e, if you define two instances in vars/main.yml, it template only for two instances and ignore for the rest.


You can test this role by issuing the below commands
yum install -y epel-release ansible
git clone git clone https://github.com/poudelpra/HAproxy.git
cd HAproxy
ansible-playbook haproxy.yml 


