## NVMe by Zabbix Agent Template

nvme-cli 2.x is not supported yet. I'm working on it

## Install

1) Install `nvme-cli` package on your server

Debian 11/Ubuntu 22.04:

```
$ sudo apt-get install nvme-cli
```

CentOS/RHEL:

```
$ yum install nvme-cli
```


2) Import the `zabbix_nvme.xml` into your Zabbix templates dashboard. This template is pre-configured and will add a new one called **NVMe by Zabbix Agent**.

3) Copy the configuration files:

```
$ cp zabbix_nvme.conf /etc/zabbix/zabbix_agentd.d/
$ cp sudoers_zabbix_nvme /etc/sudoers.d/
```

Restart Zabbix Agent
```
$ systemctl restart zabbix-agent
```
or Zabbix Agent 2

```
$ systemctl restart zabbix-agent2
```

4) Add the template to the hosts you want to monitor.

## Configuration

Override default values for following Macros depending on your hardware and personal preferences.

{$NVME_TBW_MAX} (default 300) - defines maximum TBW for (check your device documentation for this value)
{$NVME_USED_MAX} (default 80) - defines maximum value of "Percentage Used" value reported by device which triggers alert
