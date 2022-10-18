Title: Ansible installation
Date: 2022-06-01 07:00
Modified: 2022-10-18 17:00
Category: Linux
Tags: python, ansible, pip
Slug: ansible-install
Author: Tamas Molnar

# IT Automation

When I was young the System and Network Administrators wrote automation shell scripts to make their jobs faster and easier. With adding some variable parameters to these scripts a whole server system could be installed in a snap. It was the first try to automate in IT.

IT Automation is the process of reducing or replacing **direct** human interaction with the IT systems. People develop and maintain pipelines and automation code instead of the configuration files. It does not mean that companies need less people. The code for the automation must be maintained as well. Because of the complexity of these systems, sometimes there is a need for more DevOps people for the task.

Automation includes system and network automation as the main areas, and recently it is including security and monitoring as well.

IT Automation is a key in scaling faster, building reliable, self-healing systems and deploying reproducable services.

This technology helps to detect and eliminate **configuration drifts**, and the CI/CD pipelines uncover configuration errors and mistakes easily.

So do you need to learn IT automation?

In my opinion every person in IT without exception should learn the basics of IT automation.

# Ansible

[Ansible](https://www.ansible.com/) is a basic and lightweight automation and configuration management framework.

It earned the reputation of the most beginner friendly tool to learn on the market because of its initial learning curve.

Ansible is written in [Python](https://www.python.org/) and it is entirely capable of managing any size of business.

The core features of Ansible are based on the command line and they are available for anyone without buying subscriptions. Ansible is open source, the [source code](https://github.com/ansible/ansible) is managed on GitHub.

A cutting edge version of the [Ansible Automation Platform](https://www.ansible.com/products/controller?extIdCarryOver=true&sc_cid=701f2000001OH6uAAG) (previously the Ansible Tower) is available for the public, this tool is called [AWX](https://github.com/ansible/awx).

AWX gives us a web user interface, additional scheduling and role based access control to our Ansible core.

# Installing an Ansible lab

A simple Ansible management host machine can be intalled easily on any Linux machine.

Debian and Red Hat based distributions have it in their package repositories.

It's possible to install Ansible from Python PIP as well.

## Ansible in WSL

Though in the time of this post the documentation says that Ansible is not supported in WSL I haven't found any major issue with it running Ansible in my Debian.

If you want to learn the basics of Ansible automation with a minimal-effort lab, I strongly recommend starting it in WSL and later on virtual machines can help you to scale your environment.

## PIP installation

To install Ansible with Python PIP I created a venv.

It is in my project directory, so I can keep it synchronized between my WSL distros, computers and virtual machines.

```
mkdir ansible_lab                  # create a project directory
cd ansible_lab                     # change to the project directory
python3 -m venv ansible_venv       # create a virtual environment for the project in the project dir
source ansible_venv/bin/activate   # activate the venv
pip install ansible                # install Ansible and its dependencies
```

# The first steps

As a first step let's see if Ansible is installed and we see the current version.

Then let's run the first Ansible command on our local host and see if it works, try out some privilege escalation as well.

```
ansible --version
ansible localhost -m ping
ansible localhost -m ping --become --ask-become-pass
ansible localhost -m ansible.builtin.command -a "whoami" --become --ask-become-pass
```

If all command ran without problems, then the system is ready for automating with it.

# The next steps

I accept suggestions on the [Tom's IT Cafe Discord Server](https://discord.gg/4829xMBm).

# References

1. [Red Hat - What is IT automation?](https://www.redhat.com/en/topics/automation/whats-it-automation)
1. [Ansible](https://www.ansible.com/)
1. [Ansible Automation Platform 2](https://www.redhat.com/en/about/press-releases/red-hat-ansible-automation-platform-2-drives-cloud-native-automation-and-helps-developers-become-automators)
1. [Ansible documentation](https://docs.ansible.com/)