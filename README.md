# ansible-tutorial

some commands
 MAKE CHANGES TO REMOTE SERVER

ansible all -m apt -a update_cache=true --become --ask-become-pass

INSTALL PACKAGE ON REMOTE NODE EXAMPLE
ansible all -m apt -a name=vim-nox --become --ask-become-pass

ALLOWING UPGRADING PACKAGE TO LATEST IF POSSIBLE
ansible all -m apt -a "name=vim-nox state=latest" --become --ask-become-pass

UPGRADE ALL PACKAGES 
ansible all -m apt -a "upgrade=dist" --become --ask-become-pass
