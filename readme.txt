This assumes:
- running on decent mac (because we're going to create a 4cpu/4gb machine instance, and 2 smaller instances)
- vmware fusion is installed and licensed
  Using VMware Fusion Professional Version 10.0.1 (6754183).
- vagrant for vmware_fusion is installed and licensed
  Using vagrant 1.9.7.
- (optional) you have python virtual environment installed

This is not a fully-baked Ansible tower repo. It's enough to get it installed.

To start:
  vagrant up --provider=vmware_fusion

The vagrant file should do most of the work. If the version changes, you'll have to 
 modify the path then re-run 'vagrant provision'.

Once provisioned, do the following:
  vagrant ssh tower
  sudo su -
  easy_install pip
  pip install -U pip
  pip install -U ansible-tower-cli
  cd /opt/ansible-tower-setup-bundle-3.2.3-1.el7
  ./setup.sh

If it works, then you should be able to login here: https://192.168.1.100

Login with admin / password

It will prompt for license. Add the license file. Note: It appears that you can destroy and re-create
the environment and the license will work on a newly created environment.

Check out: https://192.168.1.100/api/v2


(optional) Once you have Tower licensed, you should be able to add some Tower configs.
For this, run these commands:
  virtualenv venv
  source venv/bin/activate
  pip install ansible ansible-tower-cli  (or 'pip install -r requirements.txt')
  ansible-playbook tower.yml

---

You should be able to run: (after 'vagrant up' step)
  ansible -m ping tower

You should be able to run:
  ansible-playbook playbook.yml
or
  vagrant provision

Download tower here: https://releases.ansible.com/ansible-tower/setup-bundle/

