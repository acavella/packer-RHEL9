# packer-RHEL9

## What is packer-RHEL9 ?

packer-RHEL9 is a set of configuration files used to build an automated Red Hat Enterprise Linux 9 virtual machine image using [Packer](https://www.packer.io/).
This Packer configuration file allows you to build images for VMware Workstation and Oracle VM VirtualBox.

## Prerequisites

- [Packer](https://www.packer.io/downloads.html)
  - <https://www.packer.io/intro/getting-started/install.html>
- A Hypervisor
  - [VMware Workstation](https://www.vmware.com/products/workstation-pro.html)
  - [Oracle VM VirtualBox](https://www.virtualbox.org/)

## How to use Packer

Commands to create an automated VM image:

To create a Red Hat Enterprise Linux 9 VM image using VMware Workstation use the following commands:

```cmd
cd c:\packer-RHEL9
packer build -only=vmware-iso rhel9.json
packer build -only=vmware-iso rhel9_uefi.json
```

To create a Red Hat Enterprise Linux 9 VM image using Oracle VM VirtualBox use the following commands:

```cmd
cd c:\packer-RHEL9
packer build -only=virtualbox-iso rhel9.json
packer build -only=virtualbox-iso rhel9_uefi.json
```

*If you omit the keyword "-only=" both the Workstation and Virtualbox VMs will be created.*

By default the .iso of Red Hat Enterprise Linux 9 is pulled from <https://download.rockylinux.org/pub/rocky/8/isos/x86_64/Rocky-8.6-x86_64-minimal.iso>

You can change the URL to one closer to your build server. To do so change the **"iso_url"** parameter in the **"variables"** section of the rhel9.json file.

```json
{
  "variables": {
      "iso_url": "https://download.rockylinux.org/pub/rocky/8/isos/x86_64/Rocky-8.6-x86_64-minimal.iso"
}
```

## Keyboard configuration

By default the keyboard is set to be US qwerty.
To switch it to something else edit the following file:

- ./http/ks.cfg

Set the `keyboard` parameter as desired, for example: `keyboard --vckeymap=fr --xlayouts='fr'`

## Default credentials

The default credentials for this VM image are:

|Username|Password|
|--------|--------|
|packer  |packer  |
|root    |packer  |

## Credit

Original work created by [@eaksel](https://github.com/eaksel)