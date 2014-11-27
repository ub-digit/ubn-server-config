# Ansible

## Development

```shell
vagrant up
vagrant provision
```


## Deploy

### All hosts

```shell
cd provisioning
ansible-playbook -i hosts playbook.yml --ask-sudo-pass -u <SSH användare>
```


### Limit host(s)

In this example we only want to run against webserver servers. Remove "--list-hosts" when list of host(s) are confirmed.

```shell
cd provisioning
ansible-playbook -i hosts playbook.yml --ask-sudo-pass -u <SSH användare> --limit webserver --list-hosts
```
