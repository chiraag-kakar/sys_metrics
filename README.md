# sys_metrics
---
* Track system performance statistics with `collectd`, a Unix daemon that collects system metrics periodically and provides mechanisms to store and publish the collected metrics.


* Collecting system metrics allows system administrators to monitor available resources, detect bottlenecks, and make informed decisions about servers and projects.


`collectd` is an open source daemon that collects system performance statistics periodically and provides mechanisms to store and publish the collected metrics.


## Steps to Install & Configure ( so that it knows what data to collect and how to send the values collected ) the daemon :
---
```
\\ install
sudo apt-get update
sudo apt-get install collectd
```
* After running the second command you will see the following message :

```
After this operation, 226 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

* Type Y , then hit Enter to continue installation. 

* After the installation is completed , next step is to configure the collectd plugins.

```
sudo cp /etc/collectd/collectd.conf /home/[username]/workspace/collectd.conf
sudo rm /etc/collectd/collectd.conf
sudo ln -s /home/[username]/workspace/collectd.conf /etc/collectd/collectd.conf
```

* Now edit the collectd.conf file. [Here you will be enabling certain plugins, updating paths etc.]
* So now restart `collectd` : ```sudo systemctl restart collectd```
* To check the status of collectd: ```sudo systemctl status collectd```
 
 
 Note : 
 * * If everything works fine then we should get the following message in the terminal : ```Active: active (running) ```
 * * We will also be able to see that collectd was initialized and plugins were loaded in your collectd.log file.
 
  
* Verify whether there are issues in the configuration file by running the following:
```
collectd -t ; echo $?
```
If you receive an output other than 0 then there is something wrong with collectd.conf file.

