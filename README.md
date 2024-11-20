# MASH - Ackersyndikat

Wir nutzen eine [Fork](https://github.com/shukon/mash-playbook) des [Hauptrepos](https://github.com/mother-of-all-self-hosting/mash-playbook).

Unsere Konfiguration ist verschlüsselt mittels Ansible Vault. Das Passwort liegt im Keepass.

Um dieses Playbook laufen zu lassen:

1. Klone dieses Repository, bzw. aktualisiere es mit: `git pull`
2. Im Terminal: `just roles`
3. Im Terminal: `just install-all --ask-vault-pass`
