# ELK-dhcp
Reconfigure Elasticsearch and Kibana on DHCP / Fix kipana.pid permission issue, as kibana can't create a pidfile in /var/run/ as it's running as unprivileged user.

Reconfigures Elasticsearch and Kibana on single node where IP address is changing due to DHCP.<br />
Fix for a broken kibana.pid by default install [kibana.pid permission bug](https://github.com/elastic/kibana/issues/12055)<br />
There is no need to enable Elasticsearch and Kibana services on boot as both are managed by the elastic-kibana.service unit file.<br />

Usage:<br />

place init directory to /root/<br />
chmod 700 /root/init/fix-elastic/fix-elastic.sh<br />
<br />
add systemd unit file from systemd directory to systemd by:<br />
cp elastic-kibana.service /etc/systemd/system/elastic-kibana.service<br />
sysctmctl enable elastic-kibana.service<br />
<br />
Test:<br />
systemctl start elastic-kibana.service<br />
systemctl status elastic-kibana.service<br />
<br />
Dependencies:<br />
Ansible 2.5.x<br />
