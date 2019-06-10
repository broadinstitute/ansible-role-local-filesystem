# ansible-role-local-filesystem
Ansible role - create, manage, mount local filesystems

This role expects a map of filesystems (at least one - but if none is specified
nothing is done).

Ex:

filesystems:
  - { device: '/dev/disk/by-id/google-docker', mountpoint: '/var/lib/docker' }
  - { device: '/dev/disk/by-id/data-disk', mountpoint: '/local' }


The following elements are supported for each entry:
 - device: block device to create a filesystem on and mount (no default)
 - mountpoint: directory to mount filesystem on (no default)
 - fstype: filesystem type to create.  module does not verify if it is a supported fs for the os - it will try and if not supported playbook will fail. (default: ext4)
 - mkfs_opts: any special options you want to pass to mkfs. (default: "")
 - state: state you want the file system left (deault: "mounted")


TODO:
 - fix mountoptions (empty string is not valid default)
 - ensure mountpoint exists (not usre if mount module takes care of that)

