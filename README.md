# Introduction 

This repository supplies a base setup for Odoo development using Ubuntu on Virtualbox VM provisioned by Vagrant.
The resulting environment is ready to develop with [Vim](https://www.vim.org/),
or [PyCharm](https://www.jetbrains.com/pycharm/) with a few extra steps.

## What's provided

- Ubuntu OS
- Odoo system dependencies
- Postgres configuration
- [pyenv](https://github.com/pyenv/pyenv) for python version management
- Vim development setup (code formatting, linting, autocompletion, snippets)
- Port forwarding (http, longpolling, mailhog, postgres)
- Shared folder for sync between host and guest machines

## What's not provided

- Python versions or virtualenvs (use `pyenv` to manage project specific pythons)
- Odoo source code (use `git` to manage project specific source code)
- Odoo config file (use `odoo-bin` with `--save` option to bootstrap a config)


# Dependencies

- [Virtualbox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html)

# Getting Started

- Clone the repo
- Remove the git artifacts
- Edit the Vagrantfile
- (optional) install ansible into venv if not globally installed (venv-install-ansible.sh)
- (optional) ```source venv/bin/activate```
- Run `vagrant up`

# Example

```bash
git clone https://github.com/waiteperspectives/odoo-skeleton tmp-odoo --depth 1
cd tmp-odoo
rm -rf .git
./venv-install-ansible.sh
source venv/bin/activate
vagrant up
```

