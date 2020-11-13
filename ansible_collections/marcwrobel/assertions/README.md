[![Build](https://github.com/marcwrobel/ansible-collection-assertions/workflows/CI/badge.svg)](https://github.com/marcwrobel/ansible-collection-assertions/actions)

# Ansible Collection - marcwrobel.assertions

A reusable collection of assertions for Ansible.

The main purpose of this collection is reducing the boilerplate code and displaying meaningful messages when writing [Ansible Molecule tests](https://github.com/ansible-community/molecule)
with the (default) Ansible test verifier. It can also be used to ensure a playbook cannot be run if certain conditions are not met.

This collection provides the following assertions :

https://github.com/marcwrobel/ansible-collection-assertions/blob/cleanup-and-doc/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md
- [`marcwrobel.assertions.assert_that_ansible`](/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md) - assertions on Ansible
  (`has_min_version`, `has_max_version`).
- [`marcwrobel.assertions.assert_that_distribution`](/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md) - assertions on
  distributions (`is_in`).
- [`marcwrobel.assertions.assert_that_file`](/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md) - assertions on files
  (`has_content_matching`).
- [`marcwrobel.assertions.assert_that_path`](/ansible_collections/marcwrobel/assertions/roles/assert_that_path/README.md) - assertions for paths (`exists`,
  `has_type`, `has_mode`, `has_owner`, `has_group`).
- [`marcwrobel.assertions.assert_that_service`](/ansible_collections/marcwrobel/assertions/roles/assert_that_service/README.md) - assertions on services
  (`exists`, `has_state`, `has_status`).

## Examples

### [`marcwrobel.assertions.assert_that_ansible`](/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md)

```yaml
- name: 'Assert that Ansible version is 2.8.x or 2.9.x'
  include_role:
    name: 'marcwrobel.assertions.assert_that_ansible'
  vars:
    has_min_version: '2.8'
    has_max_version: '2.10'
```

The full `marcwrobel.assertions.assert_that_ansible` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md).

### [`marcwrobel.assertions.assert_that_distribution`](/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md)

```yaml
- name: 'Assert that the distribution is supported'
  include_role:
    name: 'marcwrobel.assertions.assert_that_distribution'
  vars:
    is_in: [ 'Debian', 'RedHat 8', 'Ubuntu 20.04' ]
```

The full `marcwrobel.assertions.assert_that_distribution` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md).

### [`marcwrobel.assertions.assert_that_file`](/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md)

```yaml
- name: 'Assert that /tmp/test is managed by Ansible'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    path: '/path/to/file'
    has_content_matching: '^# Ansible managed'
```

The full `marcwrobel.assertions.assert_that_file` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md).

### [`marcwrobel.assertions.assert_that_path`](/ansible_collections/marcwrobel/assertions/roles/assert_that_path/README.md)

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

The full `marcwrobel.assertions.assert_that_path` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_path/README.md).

### [`marcwrobel.assertions.assert_that_service`](/ansible_collections/marcwrobel/assertions/roles/assert_that_service/README.md)

```yaml
- name: 'Assert that firewalld.service exists, is running and is enabled'
  include_role:
    name: 'marcwrobel.assertions.assert_that_service'
  vars:
    name: 'firewalld.service'
    has_state: 'running'
    has_status: 'enabled'
```

The full `marcwrobel.assertions.assert_that_service` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_service/README.md).
