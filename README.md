# local-ansible-provisioning

Environment to develop ansible playbooks and test their provisioning locally. Inspired by Ham Vocke's [blog post](https://www.hamvocke.com/blog/local-ansible-testing/).

Uses [vagrant](https://www.vagrantup.com/) to spin up a local VM, [ansible](https://www.ansible.com/) for provisioning and [serverspec](https://serverspec.org/) to verify that everything works as expected.

## Usage

### Develop your ansible playbook

1. Edit ansible playbook [local.yml](local.yml) and make desired changes
2. Edit tests and make desired changese
3. Spin up VM, start provisioning and tests:

```zsh
vagrant up
```

3. To rerun:

```zsh
vagrant provision
```

When you're finished, clean up with `vagrant destroy -f`

### Use your developed ansible playbook for remote provisioning

1. Edit [hosts](hosts) and enter remote IP for your server
2. Copy [local.yml](local.yml) to [remote.yml](remote.yml)
4. Edit [remote.yml](remote.yml) as desired (e.g. set `hosts: ome-other-server` and `connection: ssh`)
5. Run ansible playbook:

```zsh
ansible-playbook remote.yml -u root -i hosts
```
