[![Build](https://github.com/marcwrobel/ansible-collection-assertions/workflows/CI/badge.svg)](https://github.com/marcwrobel/ansible-collection-assertions/actions)

# Ansible Collection - marcwrobel.assertions

A reusable collection of assertions for Ansible.

The main purpose of this library is reducing the boilerplate code and displaying meaningful messages when writing [Ansible Molecule tests](https://github.com/ansible-community/molecule) tests
with the (default) Ansible test verifier.

## Supported assertions

This collection supports the following assertions :

- [assert_ansible](/ansible_collections/marcwrobel/assertions/roles/assert_ansible/README.md): Assertions on the current Ansible version.
- [assert_distribution](/ansible_collections/marcwrobel/assertions/roles/assert_distribution/README.md): Assertions on the current distribution version: name,
  version.
- [assert_file_content](/ansible_collections/marcwrobel/assertions/roles/assert_file_content/README.md): Assertions on file content.
- [assert_path](/ansible_collections/marcwrobel/assertions/roles/assert_path/README.md): Assertions on paths : existence, type, mode, owner, group.
- [assert_service](/ansible_collections/marcwrobel/assertions/roles/assert_service/README.md): Assertions on services : existence, state, status.

Take a look at each assertion README for a more comprehensible documentation with usages.
