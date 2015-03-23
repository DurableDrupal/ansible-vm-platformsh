# Installs DurableDrupalDistro Distro 

Ansible playbook for setting up a VM on your laptop or local workstation using Vagrant and VirtualBox for use with a Platform.sh project. Installs [Platform.sh CLI](https://docs.platform.sh/overview/platform-cli/) and all dependencies, and creates a database and editable virtual host to run your project locally.

Once `vagrant up` is run (down below) provisioning has installed CLI, and you are all set to `platform` and `project:get` your project from platform.sh, and you can build it locally with the following virutalhost and database:

### virtualhost

````
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName platformshvk.dev
    ServerAlias www.platformshvk.dev
    DocumentRoot /var/www/platformsh-vk-dev
    <Directory "/var/www/platformsh-vk-dev">
        Options FollowSymLinks Indexes
        AllowOverride All
    </Directory>
</VirtualHost>
````

### Database

````
$databases = array (
  'default' =>
  array (
    'default' =>
    array (
      'database' => 'platformshvk',
      'username' => 'root',
      'password' => '',
      'host' => 'localhost',
      'port' => '',
      'driver' => 'mysql',
      'prefix' => '',
    ),
  ),
);
````

These valaues are editable, see the playbook subdir

You can associate the URL with the IP specified in the Vagrantfile in your `/etc/hosts` file.

## General Instructions

Use [Jeff Geerling's Ansible for DevOps Drupal Quick Start Guide](https://github.com/geerlingguy/ansible-for-devops/tree/master/drupal#quick-start-guide) upon which this playbook is based.

* Install VirtualBox and Vagrant (make sure Vagrant is version 1.6.5 or later)
* Install Ansible
* Clone this project to a folder where you keep your VMs
* On the cammand-line in that folder, type `vagrant up`
* The process will take a while, on my 4GB RAM MacBook Pro it took about 5 minutes. A large part of that is the provisioning of the LAMP stack together with the checking out and installation of drush and DurableDrupalDistro.
* Associate http://platformshvk.dev with the private local machine ip set up by the Vagrantfile (192.168.19.46).
* Point your browser at http://platformshvk.dev after editing virtual host for the docroot of your project.

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
