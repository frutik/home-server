# home-server

Apply changes

```
ansible-playbook -i inventory/nl --vault-password-file ~/.vault/1.txt home-server.yml
```

Edit secrets

```
ansible-vault edit --vault-password-file ~/.vault/1.txt  environments/secrets.yml
```