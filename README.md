Demo EVPN on Cumulus Linux
========================
This Github repository contains the configuration files necessary for setting up EVPN (Ethernet VPN) using Cumulus Linux and Quagga on the [Reference Topology](http://github.com/cumulusnetworks/cldemo-vagrant).  Only Server01->Server04, Leaf01->Leaf04 and Spine01->Spine02 are used.

The flatfiles in this repository will set up a BGP unnumbered routing fabric between the leafs and spines, and will trunks between switches and the servers in that rack.




Quickstart: Run the single-attach demo
------------------------
    git clone https://github.com/cumulusnetworks/cldemo-evpn
    cd cldemo-evpn
    vagrant up oob-mgmt-server oob-mgmt-switch
    vagrant up leaf01 leaf02 leaf03 leaf04 spine01 spine02 server01 server02 server03 server04
    vagrant ssh oob-mgmt-server
    sudo su - cumulus
    ssh server01
    ping 172.16.1.104

![Topology](evpn.png)

Quickstart: Run the dual-attach (MLAG) demo
------------------------
    git clone https://github.com/cumulusnetworks/cldemo-evpn
    cd cldemo-evpn
    git checkout mlag
    vagrant up oob-mgmt-server oob-mgmt-switch
    vagrant up leaf01 leaf02 leaf03 leaf04 spine01 spine02 server01 server02 server03 server04
    vagrant ssh oob-mgmt-server
    sudo su - cumulus
    ssh server01
    ping 172.16.1.103

![Topology](mlag.png)

Quickstart: Run the DCI (Datacenter Interconnect) demo
------------------------
NOTE: Due to the size the DCI demo is only supported on KVM

    git clone https://github.com/cumulusnetworks/cldemo-evpn
    cd cldemo-evpn
    git checkout dci
    vagrant up oob-mgmt-server oob-mgmt-switch
    vagrant up
    vagrant ssh oob-mgmt-server
    sudo su - cumulus
    ssh server01
    ping 172.16.1.105

![Topology](dci.png)


Requirements
----------------------
[Vagrant](https://www.vagrantup.com/) (recommended 1.8.7)

and

[VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [KVM](http://www.linux-kvm.org/page/Downloads)

Factory-reset a device
----------------------
    vagrant destroy -f leaf01
    vagrant up leaf01

Destroy the entire topology
---------------------------
    vagrant destroy -f

KVM Support
---------------------------
By default this Vagrantfile is setup for Virtualbox.  To use this Demo for KVM use the Vagrantfile-kvm

    mv Vagrantfile-kvm Vagrantfile

All other directions remain the same

Detailed Instructions and Documentation
---------------------------------------
[EVPN Documentation](https://docs.cumulusnetworks.com/display/DOCS/Ethernet+Virtual+Private+Network+-+EVPN)
The EVPN Documentation was built around this demo and makes walking through this demo a breeze.  Please report problems with this demo using the "issues" tab above.

![Cumulus icon](cumulus-logo.png)

### Cumulus Linux
---------------------------------------
Cumulus Linux is a software distribution that runs on top of industry standard networking hardware. It enables the latest Linux applications and automation tools on networking gear while delivering new levels of innovation and ﬂexibility to the data center.

For further details please see: [cumulusnetworks.com](http://www.cumulusnetworks.com)
