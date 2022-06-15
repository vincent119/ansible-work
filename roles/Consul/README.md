
* Consul Version:  
    - 1.12.2
* Consul0 Platform: 
    - linux_amd64
* OS Base: 
  - Centos 7 
  - Ubuntu 22.04

## Consul Cluster architecture

![Screenshot](image/Consul-Architecture2.png)



consul Cluster node -- [consul-server-nodes]

| node name | ip |   
|--|--|
|c7-1  |172.16.99.207  |   
|c7-2 | 172.16.99.208| 
| c7-3  | 172.16.99.209     |  

consul Client node -- [consul-client-nodes]

| node name | ip |   
|--|--|
|db4  |172.16.99.204  |   
|db5 | 172.16.99.205| 
| db6 | 172.16.99.206     |  


-------

add ansible/hosts
```bash

[consul-server-nodes]
172.16.99.207 ansible_user=root
172.16.99.208 ansible_user=root
172.16.99.209 ansible_user=root

[consul-client-nodes]
172.16.99.204 ansible_user=vincent
172.16.99.205 ansible_user=vincent
172.16.99.206 ansible_user=vincent


```

Use in the roles:

```bash

- hosts: 
    - consul-server-nodes 
    - consul-client-nodes
  roles:
    - { role: Consul, become: yes}




```







consul members

```bash
Node  Address             Status  Type    Build   Protocol  DC   Partition  Segment
c7-1  172.16.99.207:8301  alive   server  1.12.2  2         tpe  default    <all>
c7-2  172.16.99.208:8301  alive   server  1.12.2  2         tpe  default    <all>
c7-3  172.16.99.209:8301  alive   server  1.12.2  2         tpe  default    <all>
db4   172.16.99.204:8301  alive   client  1.12.2  2         tpe  default    <default>
db5   172.16.99.205:8301  alive   client  1.12.2  2         tpe  default    <default>
db6   172.16.99.206:8301  alive   client  1.12.2  2         tpe  default    <default>
```

ref:(https://www.consul.io/commands/operator/raft)
```
consul operator raft list-peers

Node  ID                                    Address             State     Voter  RaftProtocol
c7-1  14470cae-bde8-8ed3-f3a7-cc3b02386870  172.16.99.207:8300  leader    true   3
c7-2  6064e2f4-f3f5-d7e3-fff4-4d9933c8447d  172.16.99.208:8300  follower  true   3
c7-3  08f24321-075d-e3a5-ad89-2f6edc0a08e7  172.16.99.209:8300  follower  true   3
```


Required Ports [link](https://www.consul.io/docs/install/ports)