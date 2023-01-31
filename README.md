Build image with debian image builder
Set 1 eth to have static ip
run ansible


```
ansible-galaxy collection install -r requirements.yml
ansible-playbook -l nanopi -u ed -k -e @secrets_file.enc --ask-vault-pass playbook.yml
ansible-playbook playbook.yml -l nanopi -u ed2
```

Interface ordering fix
https://github.com/pyavitz/debian-image-builder/issues/40

python3-apt     iso-codes aptitude iperf3   - ppp
  - pppoe
  - pppoeconf