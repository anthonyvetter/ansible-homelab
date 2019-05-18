# ansible-homelab
A set of Ansible playbooks that I use to boot strap a couple servers in my home lab

## How to use
1. Clone the repo
```
git clone https://github.com/anthonyvetter/ansible-homelab.git
```
2. Remove the `.example` from the `hosts` file (or copy to new file)
3. Modify the `hosts` file to suit your needs
4. Go to the `group_vars` folder and remove the `.example` from the files (or copy to new files)
5. Modify the `group_vars` files to suit your needs
6. Run the playbooks with the `--ask-become` flag (these playbooks don't store credentials)

## What they do
* These playbooks set up two servers in my home lab, a ZFS storage server and a Docker container server
* Not so much for recreating everything from scratch, these playbooks help to recover from a server failure, so they assume things like the disks in the server have a ZFS pool already.
* The playbooks are interactive and will prompt for vars during their run (like user names, passwords, and whatnot)
* `bootstrap.yml` sets up the base config for both servers
* `storage-bootstrap.yml` sets up the ZFS storage server
    * assumes a pool is already created and will prompt for pool name for import
    * Also sets up NFS shares which are modifiable in the `group_vars` files
* `docker-bootstrap.yml` sets up the docker server
    * Also modifies the `fstab` file to import shares from the storage server
