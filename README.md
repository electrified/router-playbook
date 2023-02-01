Build image with debian image builder
Set 1 eth to have static ip
run ansible


```
ansible-galaxy collection install -r requirements.yml
ansible-playbook -l nanopi -u ed -k -e @secrets_file.enc --ask-vault-pass playbook.yml
ansible-playbook -l nanopi -u ed2 -e @secrets_file.enc --ask-vault-pass playbook.yml 
```

Interface ordering fix
https://github.com/pyavitz/debian-image-builder/issues/40

MTU info
https://www.sonicwall.com/support/knowledge-base/how-can-i-optimize-pppoe-connections/170505851231244/