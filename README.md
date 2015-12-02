Description
===========

This directory contains a sample module, which extends functionality of Zabbix Agent. 

Status
======

This module is production ready.

Installation
============

```bash

	$ git clone https://github.com/cnshawncao/zabbix-module-redis.git
	$ cp -r zabbix-module-redis zabbix-x.x.x/src/modules/redis	# zabbix-x.x.x is zabbix version
```

1. run 'make' to build it. It should produce redis.so.

1. copy redis.so to the module directory, like LoadModulePath=/etc/zabbix/modules

1. change config file add line : LoadModule=redis.so

1. cp zbx_module_redis.conf to /etc/zabbix, modify it


    redis_inst_ports = 6379, 192.16.9.9:6380, 6381 

1. restart zabbix_agent daemon

1. import the zabbix template *zbx_template_redis_active.xml*

Synopsis
========

**key:** *redis.discovery*

**value:**

    {"data":[{"{#RSHOST}":"127.0.0.1","{#RSPORT}":"6379"},{"{#RSHOST}":"192.16.9.9","{#RSPORT}":"6380"},{"{#RSHOST}":"127.0.0.1","{#RSPORT}":"6381"}]}
    
**key:** *redis.status[{#RSHOST},{#RSPORT},key]*

Note
===

Note: this module only support the digit value, other key will return: ZBX_NOTSUPPORTED: Not supported key
