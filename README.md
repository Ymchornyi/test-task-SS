Here you can find my solution for the test task. Initial text for it you can find below 
______________________________________________________________________________________________________________
"Ansible-based test task.
You need to develop a small ansible framework for installing virtualization and deploying a virtual machine.
The framework should contain:
- role to configure KVM virtualization for debian host
- role to create a guest virtual machine
- role ton install nginx server on the guest virtual machine
______________________________________________________________________________________________________________
I chose Debian 11 as OS for both KVM deployment and guest VM. Due to my personal constraints I have to use single Azure based VM Ansible management/control node and target host for resources provisioning.
Setup is heavily based on libvirt and all the configuration/customization is handled by it in different ways. Guest OS is based on predefined .xml template and deployed over libvirt module in Ansible. VM image is heavily customized to achieve best possible capabilities (of course for the moment based on my knowledge) and applied workaround for SSH access for further management. For some reason sshd process wasn't able to start unless openssh-server is re-installed (tested on different distros). For testing purposes I use root account for remote management which is not the best for live environment but should be ok for testing only.
Basic parameters: image/network/vm_capacity is quite static and configured under defaults. Way to improve it is move towards prompts and variables. Credentials are also in plain-text and it can be fixed either with certificate-based authentication or Ansible-vault.
Whole project can be run on fresh Debian 11 server instalation with pre-installed packages (kvm, ansible, libvirt etc).
It is clear that here is a room for improvements and I am ready to dig into details to move forward.
