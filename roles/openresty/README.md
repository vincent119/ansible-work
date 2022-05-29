# openresty

* openresty version
  -- "1.19.9.1"
* os base
  
  -- Centos 7
  
  -- Ubuntu 22.04
  





# openresty 附加模組

### ngx_dynamic_upstream
[ ngx_dynamic_upstream github link ](https://github.com/cubicdaiya/ngx_dynamic_upstream)
### nginx-module-vts
[nginx-module-vts 參考](https://github.com/vozlt/nginx-module-vts)






### ngx_dynamic_upstream Quick Start
```sh
upstream Front_API {
  #ip_hash;
  zone zone_for_backends 1m;
  server 172.16.99.201:9000 max_fails=3 fail_timeout=2s;
 }
server {
  listen 80;
  server_name 127.0.0.1; 
  location /dynamic {
        allow 127.0.0.1;
        deny all;
        dynamic_upstream;
    } 
```
### 列出upstream明細
```sh
curl "http://127.0.0.1:80/dynamic?upstream=zone_for_backends"
server 172.16.99.201:9000;
```
### verbose
```bash
[root@centos7-3 vhost]#  curl "http://127.0.0.1:80/dynamic?upstream=zone_for_backends&verbose="
server 172.16.99.201:9000 weight=1 max_fails=3 fail_timeout=2;
```
### update_parameters
```bash
[root@centos7-3 vhost]#  curl "http://127.0.0.1:80/dynamic?upstream=zone_for_backends&server=172.16.99.201:9000&weight=10&max_fails=5&fail_timeout=5"
server 172.16.99.201:9000 weight=10 max_fails=5 fail_timeout=5;
```

### add
```bash
[root@centos7-3 vhost]# curl "http://127.0.0.1:80/dynamic?upstream=zone_for_backends&add=&server=127.0.0.1:6004"
server 172.16.99.201:9000;
server 127.0.0.1:6004;
```
### Remove
```sh
[root@centos7-3 vhost]# curl "http://127.0.0.1:80/dynamic?upstream=zone_for_backends&remove=&server=127.0.0.1:6004"
server 172.16.99.201:9000;

```


