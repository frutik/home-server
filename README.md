# home-server

Apply changes

```
ansible-playbook -i inventory/nl --vault-password-file ~/.vault/1.txt home-server.yml
```

Edit secrets

```
ansible-vault edit --vault-password-file ~/.vault/1.txt  vars/_/secrets.yml
```

Start devenv (not ready yet)

```
vagrant up

```