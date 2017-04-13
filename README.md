# ansible-playground

Uses Vagrant to create an environment for evaluating Ansible.

Two machines are created:

- ansible
  Ubuntu 16.04 with Ansible.

- target
  Ubuntu 16.04 with Python.

Use host _ansible_ to provision host _target_ using Ansible.

## How to Use

Create the environment with `vagrant up`, then `vagrant ssh ansible` into _ansible_.
`cd playground` and run Ansible against host _target_:

    ansible-playbook -i inventory playbook.yml

Modify the playbook and run again.
Have fun!

## How it Works

_target_ is added to the inventory at ~/playground/inventory and Vagrant's ssh keys
are included for logging in on _target_ via ssh.
