# Openstack Kolla Ansible

Openstack Kolla is OpenStack running on Containers.

Kolla offers production-ready containers and deployment tools for scalable, fast and upgradeable.

# Infrastructure:
 # Building
1. OS 

     +- 50GB /var/lib/docker
     +- 20GB para /
     DEMAIS deixar para VOLUME GROUP: cinder-volumes

    Preparação do disco
  
# Essentials tools  
yum install net-tools lspci nc mlocate wget vim tcpdump telnet -y

# Time sync
yum install ntp

# Update
yum update

# Firewall:

sudo systemctl disable firewalld
sudo systemctl stop firewalld 
sudo systemctl disable NetworkManager
sudo systemctl stop NetworkManager
sudo systemctl enable network
sudo systemctl start network

 
# SELinux
sed -i -e "s/SELINUX=enforcing/SELINUX=permissive/" config
 

# Installl
1. Install and upgrade pip to the latest before proceeding.
  
  yum install epel-release or yum install python-pip
  yum install python3-pip 
  pip install -U pip


2. Install the following dependencies:

  yum install python-devel libffi-devel gcc openssl-devel libselinux-python
  pip install python-openstackclient  --ignore-installed

3. Install Ansible from distribution packaging:

  yum install ansible

 
4. Use pip to install or upgrade Ansible to latest version:

/install -U ansible


5. Install Kolla-ansible and its dependencies using pip.


pip install kolla-ansible

 
6. Copy globals.yml and all-in-one files to /etc/kolla directory.

  cp -r /usr/share/kolla-ansible/etc_examples/kolla /etc/


Configure nova/libvirt to use KVM
/etc/kolla/config/nova/nova-compute.conf

[libvirt]
virt_type = kvm
cpu__mode = none


7. Deploy KOLLA-ANSIBLE 

   kolla-ansible certificates
   kolla-genpwd
   kolla-ansible -i all-in-one bootstrap-servers
   kolla-ansible prechecks -i all-in-one 
   kolla-ansible deploy -i all-in-one 
   kolla-ansible post-deploy -i all-in-one
 

 

If needed:

yum install git install yum-utils yum-plugin-priorities applydeltarpm epel-release python2-simplejson
yum install gcc libssl libffi 
yum install docker
pip install docker
pip install docker-compose
yum install python-urllib3
pip install urllib3 -U

pip list |grep docker
docker 3.5.0
docker-compose 1.22.0
docker-pycreds 0.3.0
dockerpty 0.4.1

 

Reference:
https://docs.openstack.org/kolla-ansible/latest/user/quickstart.html

 



