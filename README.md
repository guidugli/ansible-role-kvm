Ansible Role: kvm
=========

An Ansible Role that install and configure kvm on RHEL/CentOS, Fedora and Debian/Ubuntu.

Requirements
------------

The KVM hypervisor requires:
 - an Intel processor with the Intel VT-x and Intel 64 virtualization extensions for x86-based systems; or
 - an AMD processor with the AMD-V and the AMD64 virtualization extensions.

Role Variables
--------------

**Available variables are listed below, along with default values (see defaults/main.yml):**

    #kvm_network_add:
    #  - name: default22
    #    template: default22.xml.j2

Specify KVM networks to be added. The template must exist on `templates/networks` directory.

    #kvm_network_remove:
    #  - default22

Specify the name of KVM networks to be removed.

    #kvm_pool_add:
    #  - name: default22
    #    template: default22.xml.j2

Specify KVM storage pools to be added. The template must exist on `templates/pools` directory.

    #kvm_pool_remove:
    #  - default22

Specify the name of KVM storage pools to remove.

    #kvm_vm_add:
    #  - name: House
    #    template: House.xml.j2
    #    autostart: no
    #    files:
    #      - name: House.qcow2
    #        dest: /opt/House.qcow2
    #        owner: root
    #        group: root
    #        mode: '0600'

Specify KVM virtual machines to be added. The template must exist on `templates/vms` directory.

    #kvm_vm_remove:
    #  - House

Specify the name of Virtual Machines to be removed.

    #kvm_staff_use_svirt: no

Selinux boolean that Enables staff users to create and transition to sVirt domains.

    #kvm_unprivuser_use_svirt: no

Selinux boolean that enables unprivileged users to create and transition to sVirt domains.

    #kvm_virt_sandbox_use_audit: no

Selinux boolean that enables sandbox containers to send audit messages.

    #kvm_virt_sandbox_use_netlink: no

Selinux boolean that enables sandbox containers to use netlink system calls.

    #kvm_virt_sandbox_use_sys_admin: no

Selinux boolean that enables sandbox containers to use sys_admin system calls, such as mount.

    #kvm_virt_transition_userdomain: no

Selinux boolean that enables virtual processes to run as user domains.

    #kvm_virt_use_comm: no

Selinux boolean that enables virt to use serial/parallel communication ports.

    #kvm_virt_use_execmem: no

Selinux boolean that enables confined virtual guests to use executable memory and executable stack.

    #kvm_virt_use_fusefs: no

Selinux boolean that enables virt to read FUSE mounted files.

    #kvm_virt_use_nfs: no

Selinux boolean that enables virt to manage NFS mounted files.

    #kvm_virt_use_rawip: no

Selinux boolean that enables virt to interact with rawip sockets.

    #kvm_virt_use_samba: no

Selinux boolean that enables virt to manage CIFS mounted files.

    #kvm_virt_use_sanlock: no

Selinux boolean that enables confined virtual guests to interact with the sanlock.

    #kvm_virt_use_usb: no

Selinux boolean that enables virt to use USB devices.

    #kvm_virt_use_xserver: no

Selinux boolean that enables virtual machine to interact with the X Window System.

**The variables listed below do not need to be changed for targeted systems (see vars/main.yml):**

    kvm_services:

KVM service names.

    kvm_packages:

Packages required to install KVM.

Dependencies
------------

This role depends on the collection community.libvirt.

To install it, run: nsible-galaxy collection install community.libvirt

Example Playbook
----------------

    # In this example, templates/networks and templates/pools directories should be created
    # and the file defaultnetwork.xml.j2 should be copied to templates/networks and 
    # defaultpool.xml.j2 should be copied to templates/pools.

    - hosts: servers
      vars:
        kvm_network_add:
          - name: default22
            template: defaultnetwork.xml.j2
        kvm_pool_add:
          - name: default22
            template: defaultpool.xml.j2
        kvm_staff_use_svirt: no
        kvm_unprivuser_use_svirt: no
        kvm_virt_sandbox_use_audit: no
        kvm_virt_sandbox_use_netlink: no
        kvm_virt_sandbox_use_sys_admin: no
        kvm_virt_transition_userdomain: no
        kvm_virt_use_comm: no
        kvm_virt_use_execmem: no
        kvm_virt_use_fusefs: no
        kvm_virt_use_nfs: no
        kvm_virt_use_rawip: no
        kvm_virt_use_samba: no
        kvm_virt_use_sanlock: no
        kvm_virt_use_usb: no
        kvm_virt_use_xserver: no
      roles:
         - { role: guidugli.kvm }

License
-------

MIT / BSD

Author Information
------------------

This role was created in 2020 by Carlos Guidugli.
