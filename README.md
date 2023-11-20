# scriptloadblanacing
Streamlining load balancing configuration using shell and Jenkins CI/CD

Complete the [Steps](https://github.com/naqeebghazi/loadbalancerNginx) to setup 2 Apache web servers and 1 Nginx Load Balancer.

Create the EC2 instances:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/ec2.lb_ws1_ws2.png?raw=true)

Set the inboud rules for the security groups of both the load balancer and the webservers. 
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/loadbalancerInboudnRules.png?raw=true)
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/webserverInboundRules.png?raw=true)

Also good practice to change the name of all the servers. eg:
webserver1
webserver2
loadbalancer

SSH into the webservers and create the install.sh files on both:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/contentsofinstallshonBothWebserver1&2.png?raw=true)

Modify the permissions to allow execution of file:

    $ chmod +x install.sh

SSH into LoadBlanacher, create nginx.sh file:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/cat+x_nginxsh.png?raw=true)

Modify the permissions to allow execution of file:

    $ chmod +x nginx.sh

run both shell scripts on each:

Webservers: 

    $ ./install.sh <Public IP of webserver1>
    $ ./install.sh <Public IP of webserver2>

Loadbalancer:

    $ ./nginx.sh <Public IP of loadbalancer> <3.8.198.48:8000> <18.130.246.37:8000>

The 2nd and 3rd IP address + Port are that of webserver1 and webserver2 respectively.

Webservers successful installation output:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/resultsafterinstallinginstalshOnWebservers1&2.png?raw=true)

Loadbalancer successful installation output:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/LBsuccess_nginxsh.png?raw=true)

To conclude and confirm all is working go to the Public IP + Port number of:
- Webserver1
- Webserver2

And the public IP only of:
- loadbalancer


Webserver1 and 2:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/webservers1&2inBrowser.png?raw=true)

Loadbalancer in browser showing contents of Webser1 and Webser2 respectively:
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/loadbalancerBrowserwebserv1.png?raw=true)
![](https://github.com/naqeebghazi/scriptloadblanacing/blob/main/images/loadbalancerBrowserwebserv2.png?raw=true)
