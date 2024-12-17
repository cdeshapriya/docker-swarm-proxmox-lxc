
# Using proxmox `lxc` container docker swarm host

## Create the container

We assume that the container ID is 100

## Modify the container conf

Add the following configuration parametersoll

```
lxc.apparmor.profile: unconfined
lxc.cgroup2.devices.allow: an
lxc.cap.drop:
```

```
nano /etc/pve/nodes/ravan/lxc/100.conf
```

## Install docker

```
curl -fsSL https://get.docker.com | sudo sh
```

## Load the additional modules in the proxmox node 

```
# required kernel modules for proper docker swarm
# within LXC functionality
overlay
bonding
br_netfilter
iptable_mangle
iptable_nat
ip_vs
ip_vs_dh
ip_vs_ftp
ip_vs_lblc
ip_vs_lblcr
ip_vs_lc
ip_vs_nq
ip_vs_rr
ip_vs_sed
ip_vs_sh
ip_vs_wlc
ip_vs_wrr
nf_nat
xfrm_user
xt_conntrack
xt_MASQUERADE
```
```
nano /etc/modules-load.d/docker.conf
```


 
