[![Build](https://github.com/marcwrobel/ansible-collection-assertions/workflows/CI/badge.svg)](https://github.com/marcwrobel/ansible-collection-assertions/actions)

# Ansible Collection - marcwrobel.assertions

A reusable collection of assertions for Ansible.

The main purpose of this collection is reducing the boilerplate code and displaying meaningful messages when writing [Ansible Molecule tests](https://github.com/ansible-community/molecule)
with the (default) Ansible test verifier. It can also be used to ensure a playbook cannot be run if certain conditions are not met.

This collection provides the following assertions :

- [`marcwrobel.assertions.assert_that_ansible`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md) - assertions on Ansible
  (`has_min_version`, `has_max_version`).
- [`marcwrobel.assertions.assert_that_distribution`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md) - assertions on
  distributions (`is_in`).
- [`marcwrobel.assertions.assert_that_file`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md) - assertions on files
  (`has_content_matching`).
- [`marcwrobel.assertions.assert_that_path`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_path/README.md) - assertions for paths (`exists`,
  `has_type`, `has_mode`, `has_owner`, `has_group`).
- [`marcwrobel.assertions.assert_that_service`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_service/README.md) - assertions on services
  (`exists`, `has_state`, `has_status`).

## Requirements

In order to use this collection you need at least Ansible 2.9.

Roles are tested on Debian 10, Ubuntu 20.04, Centos 8, Fedora 33 and Amazon Linux 2. But they make use of basic Ansible modules (`assert`, `file`, `service`...)
so they should work on most of linux-based distributions, regardless of their version.

## Installing the collection

Install this collection locally:

```shell
ansible-galaxy collection install marcwrobel.assertions -p ./collections
```

Then you can use the roles from the collection in your playbooks.

## Using [`marcwrobel.assertions.assert_that_ansible`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md)

```yaml
- name: 'Assert that Ansible version is 2.9.x'
  include_role:
    name: 'marcwrobel.assertions.assert_that_ansible'
  vars:
    has_min_version: '2.9'
    has_max_version: '2.10'
```

The full `marcwrobel.assertions.assert_that_ansible` role documentation is available in its own [README](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md).

## Using [`marcwrobel.assertions.assert_that_distribution`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md)

```yaml
- name: 'Assert that the distribution is supported'
  include_role:
    name: 'marcwrobel.assertions.assert_that_distribution'
  vars:
    is_in: [ 'Debian', 'RedHat 8', 'Ubuntu 20.04' ]
```

The full `marcwrobel.assertions.assert_that_distribution` role documentation is available in its own [README](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md).

## Using [`marcwrobel.assertions.assert_that_file`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md)

```yaml
- name: 'Assert that /tmp/test is managed by Ansible'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    path: '/path/to/file'
    has_content_matching: '^# Ansible managed'
```

The full `marcwrobel.assertions.assert_that_file` role documentation is available in its own [README](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md).

## Using [`marcwrobel.assertions.assert_that_path`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_path/README.md)

```yaml
- name: 'Assert that /path/to/file exists, is a file, have mode 0640 and belongs to root:root'
  include_role:
    name: 'marcwrobel.assertions.assert_that_path'
  vars:
    path: '/path/to/file'
    has_type: 'file'
    has_mode: '0640'
    has_owner: 'root'
    has_group: 'root'
```

The full `marcwrobel.assertions.assert_that_path` role documentation is available in its own [README](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_path/README.md).

## Using [`marcwrobel.assertions.assert_that_service`](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_service/README.md)

```yaml
- name: 'Assert that firewalld.service exists, is running and is enabled'
  include_role:
    name: 'marcwrobel.assertions.assert_that_service'
  vars:
    name: 'firewalld.service'
    has_state: 'running'
    has_status: 'enabled'
```

The full `marcwrobel.assertions.assert_that_service` role documentation is available in its own [README](https://github.com/marcwrobel/ansible_collections/marcwrobel/assertions/roles/assert_that_service/README.md).

## Contributing

Check out the [contributing guide](https://github.com/marcwrobel/ansible-collection-assertions/blob/main/CONTRIBUTING.md) for more information.
