# nsswitch.conf
The network services switch file /etc/nsswitch.conf determines the order of 
search performed when a certain piece of information is requrested.
```text
hosts:           nis files dns
```
For each type of imformation, a list of sources could be specified, The sources
include local OS files (under /etc), NS and Network Information Service(NIS), db 
(berkeley DB) and Lightweight Directory Access protocol(LDAP)
