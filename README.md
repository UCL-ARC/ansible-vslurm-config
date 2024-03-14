# ansible-vslurm

An Ansible playbook for configuring a virtual Slurm cluster.

Meant to be used with [UCL-ARC/terraform-aws-vslurm](https://github.com/UCL-ARC/terraform-aws-vslurm).

Draws from [TACC/virtual-slurm-cluster](https://github.com/TACC/virtual-slurm-cluster).

## Setup

The playbook expects an inventory with the following groups and variables.
There may be more hosts within each group. Paths are expected to be absolute.

```yaml
all:
  children:
    c:
      hosts:
        node-basic-01:
          ansible_ssh_host: # IP address
    d:
      hosts:
        database:
          ansible_ssh_host: # IP address
    l:
      hosts:
        login:
          ansible_ssh_host: # IP address
    n:
      hosts:
        nfs-server:
          ansible_ssh_host: # IP address
    s:
      hosts:
        server:
          ansible_ssh_host: # IP address
  vars:
    cluster_vars:
      cluster_name: "" # The name of the cluster, e.g. "vslurm"
      mysql_socket: "" # Path to the mysql socket
      log_dir: "" # Path to the log directory. Usually "/var/log"
      slurm_dir: "" # Path to the Slurm directory. Usually "/etc/slurm"
      munge_dir: "" # Path to the munge directory. Usually "/etc/munge"
      epel9_gpg_key_url: "" # URL
      epel9_rpm_url: "" # URL
      username: "" # An existing user on the hosts
      user_home: "" # Path to the user's home directory. Usually "/home/username"
      root_home: "" # Path to the root user's home directory. Usually "/root"
      ssh_rsa_key_path: "" # Path to a private ssh key
    proxy_env:
      NO_PROXY: "" # URL
      http_proxy: "" # URL
      https_proxy: "" # URL
```
