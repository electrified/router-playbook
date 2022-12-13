ansible-galaxy collection install -r requirements.yml
ansible-playbook playbook.yml -l nanopi -u ed -k
ansible-playbook playbook.yml -l nanopi -u ed2