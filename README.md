[![Build](https://github.com/marcwrobel/ansible-collection-assertions/workflows/CI/badge.svg)](https://github.com/marcwrobel/ansible-collection-assertions/actions)

# Ansible Collection - marcwrobel.assertions

A reusable collection of assertions for Ansible.

The main purpose of this library is reducing the boilerplate code and displaying meaningful messages when writing [Ansible Molecule tests](https://github.com/ansible-community/molecule) tests
with the (default) Ansible test verifier.

## Assertions

This collection supports the following assertions :

- [assert_ansible_version](ansible_collections/marcwrobel/assertions/roles/assert_ansible_version/README.md): Asserts that Ansible version is between the given
  versions.

Take a look at each assertion README for a more comprehensible documentation with usages.
