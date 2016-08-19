# GoCD Server / Agent Provisioning

Vagrant configuration to provision a GoCD service using lxc
containers.

GoCD is an open-source Continuous Integration and Continuous Delivery
system.

GoCD consists of two installable components. The GoCD Server and one
or more GoCD Agents. They have a one-to-many relationship in that many
GoCD agents can connect to one GoCD Server. To do any real work, you
need at least one agent, since agents are the real builders or work
executors in the system.

## Requirements

* [vagrant](https://www.vagrantup.com/downloads.html)
* [vagrant-lxc](https://github.com/fgrehm/vagrant-lxc)

## Getting Started

``` sh
$ vagrant up gocd-server
$ vagrant up gocd-agent
```
