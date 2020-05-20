# nsswitch.conf
The network services switch file /etc/nsswitch.conf determines the order of 
search performed when a certain piece of information is requrested.
```text
hosts:           nis files dns
```
For each type of imformation, a list of sources could be specified, The sources
include local OS files (under /etc), NS and Network Information Service(NIS), db 
(berkeley DB) and Lightweight Directory Access protocol(LDAP)

# ip command
`ip [options] obj command`

options:
- s show statistic
- d show detailed info

obj includes:
- addr
- link  
- route
- neigh

command includes:
- add `ip addr add 10.0.0.2/24 dev enp3s0`
- delete
- show
- set  `ip link set enp3s0 up`
- monitor
