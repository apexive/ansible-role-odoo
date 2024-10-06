# Ansible Role: Odoo

An Ansible role to install and configure Odoo, an open-source ERP platform.

## Author Information

- Author: Alexis Yushin
- Company: Apexive (https://apexive.com)

## Requirements

This role requires Ansible 2.1 or higher. It supports Debian, Ubuntu, ArchLinux, and Enterprise Linux (EL) distributions.

The role depends on the following services:

- PostgreSQL database
- Traefik reverse proxy
- Redis (optional, for session storage)

## Role Variables

Here are some of the most important variables. For a full list, please check the `defaults/main.yml` file.

```yaml
odoo_enabled: true
odoo_identifier: odoo
odoo_version: "16.0"

odoo_routers:
  - hostname: www.example.com
    dbfilter: odoo-example
  - hostname: www.company.com
    dbfilter: odoo-company

odoo_admin_password: "your_secure_admin_password"

# Database configuration
odoo_database_hostname: "postgres_hostname"
odoo_database_port: 5432
odoo_database_name: odoo
odoo_database_username: "odoo_user"
odoo_database_password: "your_secure_db_password"

# Redis configuration (optional)
odoo_redis_hostname: "redis_hostname"
odoo_redis_port: 6379
odoo_redis_database: 11
odoo_redis_password: "your_secure_redis_password"

# Traefik integration
odoo_container_labels_traefik_enabled: true
odoo_container_labels_traefik_docker_network: "traefik_network"
odoo_container_labels_traefik_tls_certResolver: default

# Additional networks
odoo_container_additional_networks:
  - "traefik_network"
  - "postgres_network"
  - "redis_network"
```
