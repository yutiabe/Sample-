# Sample-
Hello world
Splunk setup Guild 
My splunk server is running on Alma Linux 9.6 on a KVM hypervisor
 
Do not install spunk as a root user.
Download the package:
sudo wget -O splunk-10.0.1-c486717c322b.x86_64.rpm "https://download.splunk.com/products/splunk/releases/10.0.1/linux/splunk-10.0.1-c486717c322b.x86_64.rpm"
provide passwd for the splunk user:
 
Install the package  as a splunk user, this will require splunk user password
# sudo rpm -ivh splunk-10.0.1-c486717c322b.x86_64.rpm
sudo rpm -ivh splunk-10.0.1-c486717c322b.x86_64.rpm
[sudo] password for splunk:
 
Enable splunk to start at boot
cd /opt/splunk/bin
sudo ./splunk enable boot-start 
NB provide passswd for slunk user and also a new username and passwd for admin account
Change permission for splunk user 
# sudo chown -R splunk:splunk /opt/splunk
# If you encounter any issue and want to change anything, Make sure to stop splunk services before making the change
sudo /opt/splunk/bin/splunk stop
sudo systemctl start Splunkd
sudo /opt/splunk/bin/splunk enable boot-start -systemd-managed 1 -user splunk
Check the firewall status
sudo systemctl status firewalld
The most common Splunk ports are:
8000/tcp: The default port for the Splunk Web interface.
8089/tcp: The management port used for communication between Splunk components (e.g., search heads, indexers, and forwarders).
9997/tcp: The default port for receiving data from Splunk universal forwarders. 
You must add these ports to the public firewall zone. The --permanent flag ensures the rule persists after a server reboot.
# Open the Splunk Web port
sudo firewall-cmd --zone=public --add-port=8000/tcp --permanent
# Open the Splunk management port
sudo firewall-cmd --zone=public --add-port=8089/tcp --permanent
# Open the Splunk forwarder receiving port
sudo firewall-cmd --zone=public --add-port=9997/tcp –permanent
Reload the firewall
#sudo firewall-cmd --reload
Go to your web browser , open a new tap
Enter the server ip and the port number eg( 10.0.0.25:8000)
Dashboard 
 

git fetch origin
git checkout 1-my-splunk-server-is-running-on-alma-linux-96-on-a-kvm-hypervisor

