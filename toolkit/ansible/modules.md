#模块列表

- [Cloud Modules](#Cloud Modules)----[官方链接](http://docs.ansible.com/list_of_cloud_modules.html)
- [Commands Modules](#Commands Modules)----[官方链接](http://docs.ansible.com/list_of_commands_modules.html)
- [Database Modules](#Database Modules)----[官方链接](http://docs.ansible.com/list_of_database_modules.html)
- [Files Modules](#Files Modules)----[官方链接](http://docs.ansible.com/list_of_files_modules.html)
- [Inventory Modules](#Inventory Modules)----[官方链接](http://docs.ansible.com/list_of_inventory_modules.html)
- [Messaging Modules](#Messaging Modules)----[官方链接](http://docs.ansible.com/list_of_messaging_modules.html)
- [Monitoring Modules](#Monitoring Modules)----[官方链接](http://docs.ansible.com/list_of_monitoring_modules.html)
- [Network Modules](#Network Modules)----[官方链接](http://docs.ansible.com/list_of_network_modules.html)
- [Notification Modules](#Notification Modules)----[官方链接](http://docs.ansible.com/list_of_notification_modules.html)
- [Packaging Modules](#Packaging Modules)----[官方链接](http://docs.ansible.com/list_of_packaging_modules.html)
- [Source Control Modules](#Source Control Modules)----[官方链接](http://docs.ansible.com/list_of_source_control_modules.html)
- [System Modules](#System Modules)----[官方链接](http://docs.ansible.com/list_of_system_modules.html)
- [Utilities Modules](#Utilities Modules)----[官方链接](http://docs.ansible.com/list_of_utilities_modules.html)
- [Web Infrastructure Modules](#Web Infrastructure Modules)----[官方链接](http://docs.ansible.com/list_of_web_infrastructure_modules.html)
- [Windows Modules](#Windows Modules)----[官方链接](http://docs.ansible.com/list_of_windows_modules.html)

##Cloud Modules <span id="Cloud Modules"/>

Amazon
- cloudformation - create a AWS CloudFormation stack
- ec2 - create, terminate, start or stop an instance in ec2
- ec2_ami - create or destroy an image in ec2
- ec2_ami_search - Retrieve AWS AMI information for a given operating system.
- ec2_asg - Create or delete AWS Autoscaling Groups
- ec2_eip - associate an EC2 elastic IP with an instance.
- ec2_elb - De-registers or registers instances from EC2 ELBs
- ec2_elb_lb - Creates or destroys Amazon ELB.
- ec2_facts - Gathers facts about remote hosts within ec2 (aws)
- ec2_group - maintain an ec2 VPC security group.
- ec2_key - maintain an ec2 key pair.
- ec2_lc - Create or delete AWS Autoscaling Launch Configurations
- ec2_metric_alarm - Create/update or delete AWS Cloudwatch ‘metric alarms’
- ec2_scaling_policy - Create or delete AWS scaling policies for Autoscaling groups
- ec2_snapshot - creates a snapshot from an existing volume
- ec2_tag - create and remove tag(s) to ec2 resources.
- ec2_vol - create and attach a volume, return volume id and device map
- ec2_vpc - configure AWS virtual private clouds
- elasticache - Manage cache clusters in Amazon Elasticache.
- rds - create, delete, or modify an Amazon rds instance
- rds_param_group - manage RDS parameter groups
- rds_subnet_group - manage RDS database subnet groups
- route53 - add or delete entries in Amazons Route53 DNS service
- s3 - S3 module putting a file into S3.

Azure
- azure - create or terminate a virtual machine in azure

Digital Ocean
- digital_ocean - Create/delete a droplet/SSH_key in DigitalOcean
- digital_ocean_domain - Create/delete a DNS record in DigitalOcean
- digital_ocean_sshkey - Create/delete an SSH key in DigitalOcean

Docker
-  docker - manage docker containers

Google
- gc_storage - This module manages objects/buckets in Google Cloud Storage.
- gce - create or terminate GCE instances
- gce_img (E) - utilize GCE image resources
- gce_lb - create/destroy GCE load-balancer resources
- gce_net - create/destroy GCE networks and firewall rules
- gce_pd - utilize GCE persistent disk resources

Linode
-  linode - create / delete / stop / restart an instance in Linode Public Cloud

Misc
- ovirt (E) - oVirt/RHEV platform management
- virt (E) - Manages virtual machines supported by libvirt

Openstack
- glance_image - Add/Delete images from glance
- keystone_user - Manage OpenStack Identity (keystone) users, tenants and roles
- nova_compute - Create/Delete VMs from OpenStack
- nova_keypair - Add/Delete key pair from nova
- quantum_floating_ip - Add/Remove floating IP from an instance
- quantum_floating_ip_associate - Associate or disassociate a particular floating IP with an instance
- quantum_network - Creates/Removes networks from OpenStack
- quantum_router - Create or Remove router from openstack
- quantum_router_gateway - set/unset a gateway interface for the router with the specified external network
- quantum_router_interface - Attach/Dettach a subnet’s interface to a router
- quantum_subnet - Add/remove subnet from a network

Rackspace
- rax - create / delete an instance in Rackspace Public Cloud
- rax_cbs - Manipulate Rackspace Cloud Block Storage Volumes
- rax_cbs_attachments - Manipulate Rackspace Cloud Block Storage Volume Attachments
- rax_cdb - create/delete or resize a Rackspace Cloud Databases instance
- rax_cdb_database - create / delete a database in the Cloud Databases
- rax_cdb_user - create / delete a Rackspace Cloud Database
- rax_clb - create / delete a load balancer in Rackspace Public Cloud
- rax_clb_nodes - add, modify and remove nodes from a Rackspace Cloud Load Balancer
- rax_dns - Manage domains on Rackspace Cloud DNS
- rax_dns_record - Manage DNS records on Rackspace Cloud DNS
- rax_facts - Gather facts for Rackspace Cloud Servers
- rax_files - Manipulate Rackspace Cloud Files Containers
- rax_files_objects - Upload, download, and delete objects in Rackspace Cloud Files
- rax_identity - Load Rackspace Cloud Identity
- rax_keypair - Create a keypair for use with Rackspace Cloud Servers
- rax_meta - Manipulate metadata for Rackspace Cloud Servers
- rax_network - create / delete an isolated network in Rackspace Public Cloud
- rax_queue - create / delete a queue in Rackspace Public Cloud
- rax_scaling_group - Manipulate Rackspace Cloud Autoscale Groups
- rax_scaling_policy - Manipulate Rackspace Cloud Autoscale Scaling Policy

Vmware
- vsphere_guest - Create/delete/manage a guest VM through VMware vSphere.



##Commands Modules <span id="Commands Modules"/>

- command - Executes a command on a remote node
- raw - Executes a low-down and dirty SSH command
- script - Runs a local script on a remote node after transferring it
- shell - Execute commands in nodes.

##Database Modules <span id="Database Modules"/>

Misc
- mongodb_user (E) - Adds or removes a user from a MongoDB database.
- redis (E) - Various redis commands, slave and flush
- riak (E) - This module handles some common Riak operations

Mysql
- mysql_db - Add or remove MySQL databases from a remote host.
- mysql_replication (E) - Manage MySQL replication
- mysql_user - Adds or removes a user from a MySQL database.
- mysql_variables - Manage MySQL global variables

Postgresql
- postgresql_db - Add or remove PostgreSQL databases from a remote host.
- postgresql_privs - Grant or revoke privileges on PostgreSQL database objects.
- postgresql_user - Adds or removes a users (roles) from a PostgreSQL database.
- postgresql_lang (E) - Adds, removes or changes procedural languages with a PostgreSQL database.

##Files Modules <span id="Files Modules" />

- acl - Sets and retrieves file ACL information.
- assemble - Assembles a configuration file from fragments
- copy - Copies files to remote locations.
- fetch - Fetches a file from remote nodes
- file - Sets attributes of files
- ini_file - Tweak settings in INI files
- lineinfile - Ensure a particular line is in a file, or replace an existing line using a back-referenced regular expression.
- patch (E) - Apply patch files using the GNU patch tool.
- replace - Replace all instances of a particular string in a file using a back-referenced regular expression.
- stat - retrieve file or file system status
- synchronize - Uses rsync to make synchronizing file paths in your playbooks quick and easy.
- template - Templates a file out to a remote server.
- unarchive - Copies an archive to a remote location and unpack it
- xattr - set/retrieve extended attributes

##Inventory Modules <span id="Inventory Modules" />

- add_host - add a host (and alternatively a group) to the ansible-playbook in-memory inventory
- group_by - Create Ansible groups based on facts

##Messaging Modules <span id="Messaging Modules" />

- rabbitmq_parameter (E) - Adds or removes parameters to RabbitMQ
- rabbitmq_plugin (E) - Adds or removes plugins to RabbitMQ
- rabbitmq_policy (E) - Manage the state of policies in RabbitMQ.
- rabbitmq_user (E) - Adds or removes users to RabbitMQ
- rabbitmq_vhost (E) - Manage the state of a virtual host in RabbitMQ

##Monitoring Modules <span id="Monitoring Modules" />

- airbrake_deployment (E) - Notify airbrake about app deployments
- bigpanda (E) - Notify BigPanda about deployments
- boundary_meter (E) - Manage boundary meters
- datadog_event (E) - Posts events to DataDog service
- librato_annotation (E) - create an annotation in librato
- logentries (E) - Module for tracking logs via logentries.com
- monit (E) - Manage the state of a program monitored via Monit
- nagios (E) - Perform common tasks in Nagios related to downtime and notifications.
- newrelic_deployment (E) - Notify newrelic about app deployments
- pagerduty (E) - Create PagerDuty maintenance windows
- pingdom (E) - Pause/unpause Pingdom alerts
- rollbar_deployment (E) - Notify Rollbar about app deployments
- stackdriver (E) - Send code deploy and annotation events to stackdriver
- uptimerobot (E) - Pause and start Uptime Robot monitoring
- zabbix_group (E) - Add or remove a host group to Zabbix.
- zabbix_maintenance (E) - Create Zabbix maintenance windows

##Network Modules <span id="Network Modules" />

- dnsimple (E) - Interface with dnsimple.com (a DNS hosting service).
- dnsmadeeasy (E) - Interface with dnsmadeeasy.com (a DNS hosting service).
- haproxy (E) - An Ansible module to handle states enable/disable server and set weight to backend host in haproxy using socket commands.
- lldp (E) - get details reported by lldp
- openvswitch_bridge (E) - Manage Open vSwitch bridges
- openvswitch_port (E) - Manage Open vSwitch ports
- snmp_facts (E) - Retrive facts for a device using SNMP.

A10
- a10_server (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices
- a10_service_group (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices
- a10_virtual_server (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices

Basics
- get_url - Downloads files from HTTP, HTTPS, or FTP to node
- slurp - Slurps a file from remote nodes
- uri - Interacts with webservices

Citrix
- netscaler (E) - Manages Citrix NetScaler entities

F5
- bigip_facts (E) - Collect facts from F5 BIG-IP devices
- bigip_monitor_http (E) - Manages F5 BIG-IP LTM http monitors
- bigip_monitor_tcp (E) - Manages F5 BIG-IP LTM tcp monitors
- bigip_node (E) - Manages F5 BIG-IP LTM nodes
- bigip_pool (E) - Manages F5 BIG-IP LTM pools
- bigip_pool_member (E) - Manages F5 BIG-IP LTM pool members

##Notification Modules <span id="Notification Modules" />

- campfire (E) - Send a message to Campfire
- flowdock (E) - Send a message to a flowdock
- grove (E) - Sends a notification to a grove.io channel
- hipchat (E) - Send a message to hipchat
- irc (E) - Send a message to an IRC channel
- jabber (E) - Send a message to jabber user or chat room
- mail (E) - Send an email
- mqtt (E) - Publish a message on an MQTT topic for the IoT
- nexmo (E) - Send a SMS via nexmo
- osx_say (E) - Makes an OSX computer to speak.
- slack (E) - Send Slack notifications
- sns (E) - Send Amazon Simple Notification Service (SNS) messages
- twilio (E) - Sends a text message to a mobile phone through Twilio.
- typetalk (E) - Send a message to typetalk

##Packaging Modules <span id="Packaging Modules" />

Language
- bower (E) - Manage bower packages with bower
- composer (E) - Dependency Manager for PHP
- cpanm (E) - Manages Perl library dependencies.
- easy_install - Installs Python libraries
- gem - Manage Ruby gems
- npm (E) - Manage node.js packages with npm
- pip - Manages Python library dependencies.

Os
- apt - Manages apt-packages
- apt_key - Add or remove an apt key
- apt_repository - Add and remove APT repositories
- apt_rpm - apt_rpm package manager
- dnf (E) - Manages packages with the I(dnf) package manager
- homebrew (E) - Package manager for Homebrew
- homebrew_cask (E) - Install/uninstall homebrew casks.
- homebrew_tap (E) - Tap a Homebrew repository.
- layman (E) - Manage Gentoo overlays
- macports (E) - Package manager for MacPorts
- openbsd_pkg (E) - Manage packages on OpenBSD.
- opkg (E) - Package manager for OpenWrt
- pacman (E) - Manage packages with I(pacman)
- pkg5 (E) - Manages packages with the Solaris 11 Image Packaging System
- pkg5_publisher (E) - Manages Solaris 11 Image Packaging System publishers
- pkgin (E) - Package manager for SmartOS
- pkgng (E) - Package manager for FreeBSD >= 9.0
- pkgutil (E) - Manage CSW-Packages on Solaris
- portage (E) - Package manager for Gentoo
- portinstall (E) - Installing packages from FreeBSD’s ports system
- redhat_subscription - Manage Red Hat Network registration and subscriptions using the C(subscription-manager) command
- rhn_channel - Adds or removes Red Hat software channels
- rhn_register - Manage Red Hat Network registration using the C(rhnreg_ks) command
- rpm_key - Adds or removes a gpg key from the rpm db
- svr4pkg (E) - Manage Solaris SVR4 packages
- swdepot (E) - Manage packages with swdepot package manager (HP-UX)
- urpmi (E) - Urpmi manager
- yum - Manages packages with the I(yum) package manager
- zypper (E) - Manage packages on SUSE and openSUSE
- zypper_repository (E) - Add and remove Zypper repositories

##Source Control Modules <span id="Source Control Modules" />

- bzr (E) - Deploy software (or files) from bzr branches
- git - Deploy software (or files) from git checkouts
- github_hooks (E) - Manages github service hooks.
- hg - Manages Mercurial (hg) repositories.
- subversion - Deploys a subversion repository.

##System Modules <span id="System Modules" />

- alternatives (E) - Manages alternative programs for common commands
- at (E) - Schedule the execution of a command or script file via the at command.
- authorized_key - Adds or removes an SSH authorized key
- capabilities (E) - Manage Linux capabilities
- cron - Manage cron.d and crontab entries.
- crypttab (E) - Encrypted Linux block devices
- debconf (E) - Configure a .deb package
- facter (E) - Runs the discovery program I(facter) on the remote system
- filesystem (E) - Makes file system on block device
- firewalld (E) - Manage arbitrary ports/services with firewalld
- getent (E) - a wrapper to the unix getent utility
- gluster_volume (E) - Manage GlusterFS volumes
- group - Add or remove groups
- hostname - Manage hostname
- kernel_blacklist (E) - Blacklist kernel modules
- locale_gen (E) - Creates or removes locales.
- lvg (E) - Configure LVM volume groups
- lvol (E) - Configure LVM logical volumes
- modprobe (E) - Add or remove kernel modules
- mount - Control active and configured mount points
- ohai (E) - Returns inventory data from I(Ohai)
- open_iscsi (E) - Manage iscsi targets with open-iscsi
- ping - Try to connect to host and return C(pong) on success.
- seboolean - Toggles SELinux booleans.
- selinux - Change policy and state of SELinux
- service - Manage services.
- setup - Gathers facts about remote hosts
- svc (E) - Manage daemontools services.
- sysctl - Manage entries in sysctl.conf.
- ufw (E) - Manage firewall with UFW
- user - Manage user accounts
- zfs (E) - Manage zfs

##Utilities Modules <span id="Utilities Modules" />

Helper
- accelerate - Enable accelerated mode on remote node
- fireball - Enable fireball mode on remote node

Logic
- assert - Fail with custom message
- async_status - Obtain status of asynchronous task
- debug - Print statements during execution
- fail - Fail with custom message
- include_vars - Load variables from files, dynamically within a task.
- pause - Pause playbook execution
- set_fact - Set host facts from a task
- wait_for - Waits for a condition before continuing.

##Web Infrastructure Modules <span id="Web Infrastructure Modules" />

- apache2_module - enables/disables a module of the Apache2 webserver
- django_manage - Manages a Django application.
- ejabberd_user (E) - Manages users for ejabberd servers
- htpasswd - manage user files for basic authentication
- jboss (E) - deploy applications to JBoss
- jira (E) - create and modify issues in a JIRA instance
- supervisorctl - Manage the state of a program or group of programs running via supervisord

##Windows Modules <span id="Windows Modules" />

- win_chocolatey (E) - Installs packages using chocolatey
- win_feature - Installs and uninstalls Windows Features
- win_get_url - Fetches a file from a given URL
- win_group - Add and remove local groups
- win_msi - Installs and uninstalls Windows MSI files
- win_ping - A windows version of the classic ping module.
- win_service - Manages Windows services
- win_stat - returns information about a Windows file
- win_updates (E) - Lists / Installs windows updates
- win_user - Manages local Windows user accounts


