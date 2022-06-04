
# set time server

OS base: 
  - Centos 7
  - Ubuntu 22.04

chrony version:
  - latest

in defaults/main.yaml
```bash

chrony_config_server:
  - server time1.google.com iburst
  - server time2.google.com iburst
  - server time3.google.com iburst
  - server time4.google.com iburst

```


playbook example
```bash
- hosts: db3
  roles:
    - { role: Chrony , become: yes}
    
```



