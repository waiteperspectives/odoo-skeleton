# Introduction

Playbooks for deploying Odoo on Ubuntu

## Running the automation

- edit hosts.ini to point to the server
- run `ansible-playbook -i hosts.ini playbook.yaml`

## Manual steps

- pip install python dependencies
- create `odoo8069` database
- launch odoo to install base
- enable the odoo service
- configure dns
- configure certbot for ssl
