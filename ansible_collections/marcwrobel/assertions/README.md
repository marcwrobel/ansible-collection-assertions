[![Build](https://github.com/marcwrobel/ansible-collection-assertions/workflows/CI/badge.svg)](https://github.com/marcwrobel/ansible-collection-assertions/actions)

# Ansible Collection - marcwrobel.assertions

A reusable collection of assertions for Ansible.

The main purpose of this library is reducing the boilerplate code and displaying meaningful messages when writing [Ansible Molecule tests](https://github.com/ansible-community/molecule)
with the (default) Ansible test verifier. It can also be used to ensure a playbook cannot be run if certain conditions are not met.

This collection supports the following assertions :

- [`assert_that_ansible`](/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md): Assertions on Ansible (`has_min_version`,
  `has_max_version`).
- [`assert_that_distribution`](/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md): Assertions on distributions (`is_in`).
- [`assert_that_file`](/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md): Assertions on files (`has_content_matching`).
- [assert_path](/ansible_collections/marcwrobel/assertions/roles/assert_path/README.md): Assertions on paths : existence, type, mode, owner, group.
- [assert_service](/ansible_collections/marcwrobel/assertions/roles/assert_service/README.md): Assertions on services : existence, state, status.

## Examples

### `assert_that_ansible`

    - name: 'Assert that Ansible version is 2.8.x or 2.9.x'
      include_role:
        name: 'assert_that_ansible'
      vars:
        has_min_version: '2.8'
        has_max_version: '2.10'

The full `assert_that_ansible` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_ansible/README.md).

### `assert_that_distribution`

    - name: 'Assert that the distribution is supported'
      include_role:
        name: 'assert_that_distribution'
      vars:
        is_in: [ 'Debian', 'RedHat 8', `Ubuntu 20.04` ]

The full `assert_that_distribution` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_distribution/README.md).

### `assert_that_file`

    - name: 'Assert that /tmp/test is managed by Ansible'
      include_role:
        name: 'assert_that_file'
      vars:
        path: '/path/to/file'
        has_content_matching: '^# Ansible managed'

The full `assert_that_file` role documentation is available in its own [README](/ansible_collections/marcwrobel/assertions/roles/assert_that_file/README.md).
