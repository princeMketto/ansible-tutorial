# ansible-tutorial

some commands
 MAKE CHANGES TO REMOTE SERVER

ansible all -m gather_facts --limit ip-address

TO GATHER Facts -only distribution details (somthing similar to cat /etc/os-release)
ansible all -m gather_facts --limit 192.168.100.5 | grep ansible_distribution

ansible all -m apt -a update_cache=true --become --ask-become-pass

INSTALL PACKAGE ON REMOTE NODE EXAMPLE
ansible all -m apt -a name=vim-nox --become --ask-become-pass

ALLOWING UPGRADING PACKAGE TO LATEST IF POSSIBLE
ansible all -m apt -a "name=vim-nox state=latest" --become --ask-become-pass

UPGRADE ALL PACKAGES 
ansible all -m apt -a "upgrade=dist" --become --ask-become-pass

RUNNING PLAYBOOK
ansible-playbook --ask-become-pass install_apache.yml

INSTALLING PACKAGE INTO MACHINES WITH DIFFERENT PLATFORM. eg. UBUNTU and CENTOS
// this is where  a "when" statement comes in
eg.
  - name: installing apache2 package
    apt:
      name: apache2
      state: latest
    when: ansible_distribution == "Ubuntu" and ansible_distribution_versino == "8.2" ( use and to add more) 


>>To specify multiple platform use in instead of == eg: when: ansible_distribution in  ["Ubuntu","Debian"]
