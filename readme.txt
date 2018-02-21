To start:
  vagrant up --provider=vmware_fusion

Ensure you can run:
  ansible -m ping tower

Ensure you can run:
  ansible-playbook playbook.yml
or
  vagrant provision

Todo:
- setup inventory file
