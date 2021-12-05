![example workflow](https://github.com/infrastructr/ansible-role-rancher-master/actions/workflows/main.yml/badge.svg)
[![Ansible Galaxy](https://img.shields.io/badge/role-infrastructr.rancher_master-blue.svg)](https://galaxy.ansible.com/infrastructr/rancher_master/)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/infrastructr/ansible-role-rancher-master)](https://galaxy.ansible.com/infrastructr/rancher_master)
[![Ansible Galaxy Downloads](https://img.shields.io/ansible/role/d/49670.svg?color=blue)](https://galaxy.ansible.com/infrastructr/rancher_master/)

# Ansible Role: Rancher Master

An Ansible Role that manages setup and configuration of an [Rancher](https://rancher.com/docs/rancher/v2.x/en/installation/) master.

## Role Variables

Available variables listed below, along with default values (see `defaults/main.yml`):

    rancher_master_group: paas_master

Inventory group for the Rancher master hosts.

    rancher_master_base_group: paas

Inventory group for all Rancher hosts.        

    rancher_master_version: v2.4.5
    
Rancher server version.
    
    rancher_master_host: "{{ hostvars[groups[rancher_master_group][0]]['ansible_host'] }}"
    
Rancher API host.    
    
    rancher_master_url: "https://{{ rancher_master_host }}"
    
Rancher API URL.    
    
    rancher_master_admin_password: secret    

Rancher admin password.   
    
    rancher_master_admin_password_default: admin
   
Initial Rancher admin password that is subject to change.

    rancher_master_validate_certs: no
    
Enable/disable SSL certificate validation when communicating with the Rancher API.

    rancher_master_ssl: generated-selfsigned

Rancher server SSL certificate mode. Defaults to the auto generated self signed SSL certificate. Specify `generated-letsencrypt` to use Let's Encrypt SSL certificate generation.

    rancher_master_retries: 10
    
Number of retries for long-running operations.

    rancher_master_delay: 30
    
Number of seconds as delay between retries for long-running operations.

    rancher_master_volume: paas_master_volume # or /opt/rancher
    
Rancher master volume is for persistent data and it could be either named volume or path on the host.


## Dependencies

None.

## Example Playbook

    - hosts: all
      vars:
        pip_package: python3-pip
        pip_install_packages:
          - name: docker    
      roles:
        - geerlingguy.pip
        - geerlingguy.docker    
        - infrastructr.rancher_master

## Development

Use [docker-molecule](https://github.com/infrastructr/docker-molecule) following the instructions to run [Molecule](https://molecule.readthedocs.io/en/stable/)
or install [Molecule](https://molecule.readthedocs.io/en/stable/) locally (not recommended, version conflicts might appear).

Provide Hetzner Cloud token:

    export HCLOUD_TOKEN=123abc456efg

Use following to run tests:

    molecule test --all

## Maintainers

- [build-failure](https://github.com/build-failure)

## License

See the [LICENSE.md](LICENSE.md) file for details.

## Author Information

This role was created in 2020 by [infrastructr](https://github.com/infrastructr) team.
