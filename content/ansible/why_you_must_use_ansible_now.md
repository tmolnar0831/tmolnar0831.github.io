Title: Why you must learn and use Ansible now?
Date: 2022-10-13 07:00
Modified: 2022-10-13 07:00
Category: Linux
Tags: python, ansible, automation
Slug: why-you-must-use-ansible-now
Author: Tamas Molnar

# Ansible

[Ansible](https://docs.ansible.com/ansible-core/devel/index.html) is a lightweight, easy-to-use configuration management and orchestration framework. It can connect to the hosts on different channels, like on sockets or through network.

Ansible is radically simple as it uses YAML for structuring its command files called "[playbooks](https://docs.ansible.com/ansible-core/devel/playbook_guide/index.html)".

It is an [open source project](https://github.com/ansible/ansible) developed by Red Hat.

Without proper configuration management a simple configuration drift can cause serious distruptions.
Most of the time the configuration just grows incrementally till a point where noone knows the reasons behind decisions.

With configuration as code (infrastructure as code) the administrators check in the configurations into source control management like Git.
They may feel it a bit of overhead initially, but the reward is a commented history of the evolution of the configuration. Every change has a reason and it gets journaled in a searchable form. Configuration changes are revertable easily.

# Docker

The other day I heard something that caught my attention: someone said during a meeting that "Ansible is the past..." and later I heard "...we must use Docker instead".

I can only pay attention to my blog after the office hours, so I had time to calm down, so I will not write my initial ideas.

In nutshell:

1. Docker != Configuration Management
1. Ansible != Container Technology

Docker is an Open Source container technology based on the kernel cgroups.

Based on my experience with Docker and with a private registry, it is recommended to keep the base images small and simple as much as possible.

With complex image building processes the error rate grew exponentionally. The size of the images can be large, and it is more difficult to find the bugs.