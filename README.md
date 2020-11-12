[![Build](https://github.com/marcwrobel/ansible-collection-assertions/workflows/CI/badge.svg)](https://github.com/marcwrobel/ansible-collection-assertions/actions)

# Ansible Collection - marcwrobel.assertions

A reusable collection of assertions for Ansible.

The main purpose of this library is reducing the boilerplate code and displaying meaningful messages when writing [Ansible Molecule tests](https://github.com/ansible-community/molecule) tests
with the (default) Ansible test verifier.

## Provided assertions

- [assert.ansible_version](ansible_collections/marcwrobel/assertions/roles/assert_ansible_version/README.md).

## Tips & tricks

### Testing versions

Testing version strings is simple using the [`version` test](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions).

For instance :

    assert:
      that:
        - "ansible_version.full is version('2.8', '>=')"
        - "ansible_version.full is version('2.8', '<=')"

## Links
- [Ansible documentation - Tests](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html)
