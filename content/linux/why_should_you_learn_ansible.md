Title: Why should you learn and use Ansible right now?
Date: 2022-10-13 07:00
Modified: 2022-10-18 17:00
Category: Linux
Tags: python, ansible, automation
Slug: why-should-you-learn-ansible-now
Author: Tamas Molnar
Status: draft

Whether you have some devices at home, you operate a small office with a couple of computers or you are one of the sysadmins in a large organization, Ansible can work for you (or instead of you).

[Ansible](https://docs.ansible.com/ansible-core/devel/index.html) is a lightweight but very powerful configuration management and orchestration framework. It can connect to the hosts on different channels, like network-cli, netconf or through SSH.

Ansible is radically simple, it uses YAML for structuring its command files called "[playbooks](https://docs.ansible.com/ansible-core/devel/playbook_guide/index.html)".

It is an [open source project](https://github.com/ansible/ansible) backed and developed by Red Hat.

![Ansible](../images/ansible_logo.png "Ansible logo")

I don't have to explain what does it mean not to use SCM and config management.

Without proper configuration management a simple configuration drift can cause serious service distruptions.
Most of the time the configuration of an infrastructure just grows incrementally until a point where nobody knows the reasons behind changes. There can be multiple instances of configuration files for a service with slighty different style and data. This causes confusion and major issues. The solution for this more-than-a-decade-old problem was writing scripts for configuration managment. Over the years it evolved to invent tools like [CFEngine](https://cfengine.com/), [Puppet](https://puppet.com/), [Chef](https://www.chef.io/), [Salt](https://saltproject.io/) and [Ansible](https://www.ansible.com/). There are more to mention, but these were the top competitors of the market for long. Both tools went over an evolution, and they targeted different styles of operations. Ansible is simple with a possibility to extend the system as it evolves.

You can install Ansible on your Windows notebook using WSL2 and it can be used to manage any home and/or office infrastructure in a snap. Later on the whole code base can be moved easily to a central Ansible host from where the management can happen. From an easy-to-use and easy-to-understand system the evolution will lead you to use roles and variables till a pont to use Ansible Vault (or later more sophisticated credential management tools). The roles, inventories and (public) variable files can be stored in central source control management as GitLab or GitHub. With minimal effor you are doing infrastructure as code.

With infrastructure as code the administrators push the configurations into source control management. Every change in the configuration is timestamped, logged and commented for avoiding the later confusion. It is very useful even in your home network.

This approach may feel a bit of overhead initially, but the reward is huge. Every change has a reason, and it is stored in a searchable form. Configuration changes become revertable easily.

Ansible helps to avoid configuration drifts too. It effectively automates the repetitive tasks. On the other hand Ansible helps to separate different layers of the operations like credential/secret management, variables and infrastructure code.

Summarizing the thoughts above:

- Ansible is a simple config management and orchestration framework.
- It helps to standardize the configuration handling.
- It manages the automation of repetitive tasks.
- Ansible can scale with your knowledge and with the size of the managed system as well.
- Ansible is an open source project available on GitHub.

If you want to share your comments or thoughts, join the [Tom's IT Cafe Discord Server here](https://discord.gg/4829xMBm)!