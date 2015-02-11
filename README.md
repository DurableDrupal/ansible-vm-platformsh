# Installs DurableDrupalDistro Distro 

Ansible playbook for setting up [Durable Drupal Distro](https://github.com/DurableDrupal/durable-drupal-distro) on local workstation using Vagrant and VirtualBox based on the drupallean profile.

## Instructions

Use [Jeff Geerling's Ansible for DevOps Drupal Quick Start Guide](https://github.com/geerlingguy/ansible-for-devops/tree/master/drupal#quick-start-guide) upon which this playbook is based.

* Install VirtualBox and Vagrant (make sure Vagrant is version 1.6.5 or later)
* Install Ansible
* Clone this project to a folder where you keep your VMs
* On the cammand-line in that folder, type `vagrant up`
* The process will take a while, on my 4GB RAM MacBook Pro it took about 5 minutes. A large part of that is the provisioning of the LAMP stack together with the checking out and installation of drush and DurableDrupalDistro.
* Associate http://durabledrupalwebsite.dev/ with the private local machine ip set up by the Vagrantfile (192.168.34.11).
* Point your browser at http://durabledrupalwebsite.dev/user and login with user admin and password admin
* Very little to look at more than a stark Adaptivetheme subtheme called drupallean
* Check out http://durabledrupalwebsite.dev/admin/modules

The vagrant init was originally done with:
$ vagrant init ubuntu/trusty64

Which created a new vagrant file based on the latest ubuntu image (see Vagrant & Ansible Quickstart Tutorial below)

downloading:

https://vagrantcloud.com/ubuntu/boxes/trusty64/versions/14.04/providers/virtualbox.box

#### References

* [Geerling, Jeff, *Ansible for DevOps*](https://leanpub.com/ansible-for-devops)
  * [Ansible for DevOps Examples on GitHub](https://github.com/geerlingguy/ansible-for-devops)
* [Vagrant & Ansible Quickstart Tutorial](http://adamcod.es/2014/09/23/vagrant-ansible-quickstart-tutorial.html)
* [*defunct* Configurar Servidores Es Sencillo Con Ansible](http://guate2014.drupal-centroamerica.org/session/configurar-servidores-es-sencillo-con-ansible)
  * [axai-mx/ansible-drupal-roles](https://github.com/axai-mx/ansible-drupal-roles)
  * [Setup de ambiente de desarrollo (ubuntu / debian)](http://www.axai.com.mx/es/blog/setup-de-ambiente-de-desarrollo-ubuntu-debian)
  * [How To Set Up Your Linode](http://feross.org/how-to-setup-your-linode/)
