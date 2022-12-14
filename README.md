ansible-galaxy collection install -r requirements.yml
ansible-playbook playbook.yml -l nanopi -u ed -k
ansible-playbook playbook.yml -l nanopi -u ed2

Interface ordering fix
https://github.com/pyavitz/debian-image-builder/issues/40