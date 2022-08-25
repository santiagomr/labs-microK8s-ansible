# Kubernetes lab deployed with Ansible and MicroK8s

This project is capable of easily and automatically initializing a laboratory MicroK8s cluster with N nodes (VirtualBox VMs) with the aim of experimenting and developing on this orchestration technology.

To do this, it uses a multi-machine Vagrantfile and an Ansible playbook capable of installing MicroK8s and initializing the cluster (In simple words, it turns the [MicroK8s getting started documentation](https://microk8s.io/docs/getting-started) into an Ansible playbook).

The vagrantfile includes constants to parameterize: total number of nodes (machines), base box, IP range of the private network and number of cores and RAM assigned to each node. The ansible provisioner is invoked only when all nodes are up and running.

## Requirements

For the execution of this project it is necessary to have the following tools installed in your host:
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (Tested on version >= 6.1.X)
- [Vagrant](https://www.vagrantup.com/downloads) (Tested on version >= 2.2.X)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) (Tested on version >= 2.10.X)


## How to use

Once the repository is cloned, simply go to the root directory of the project.

Duplicate and rename the `vars.yml.example` file to `vars.yml`. In it you can define the variables according to what you need.

```shell
labs-microK8s-ansible git:(master) ✗ cp vars.yml.example vars.yml && nano vars.yml
```

Edit the constants in the `Vagrantfile` if necessary (total number of nodes, base box, IP range of the private network and number of cores and RAM assigned to each node)

```shell
labs-microK8s-ansible git:(master) ✗ nano Vagrantfile
```

Finally, provision the environment:
```shell
labs-microK8s-ansible git:(master) ✗ vagrant up
```

That's it! You can now log into your nodes via vagrant (`vagrant ssh node1`) or directly via SSH with the correct username and IP (`ssh ubuntu@192.168.60.11`).


## License

GNU GPLv3


## Author Information

[@santiagomr](https://github.com/santiagomr)