# marcwrobel.assertions.assert_ansible_version

Assertions on [Ansible version](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#ansible-version).

This role is using the [`version` test](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions) internally : versions
comparison respects the `version` test specification.

## Role variables

This role is using the following variables:

- `min` (`string`, optional) - the minimum required Ansible version, included (`min >= ansible_version.full`).
- `max` (`string`, optional) - the maximum required Ansible version, excluded (`ansible_version.full < max`).
- `strict` (`boolean`, required, default=`false`) - whether [strict version parsing](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions))
  must be used.

## Usage

    - name: 'Assert that Ansible version is >= 2.8 and < 2.10'
      include_role:
        name: 'assert_ansible_version'
      vars:
        min: '2.8'
        max: '2.10'

    - name: 'Assert that Ansible version is >= 2.8'
      include_role:
        name: 'assert_ansible_version'
      vars:
        min: '2.8'

    - name: 'Assert that Ansible version is < 2.10'
      include_role:
        name: 'assert_ansible_version'
      vars:
        max: '2.10'

    - name: 'Assert that Ansible version is >= 2.8 and < 2.10 (strict)'
      include_role:
        name: 'assert_ansible_version'
      vars:
        min: '2.8'
        max: '2.10'
        strict: true

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - Discovering variables: facts and magic variables - Ansible version](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#ansible-version)
- [Ansible - Tests - Comparing versions](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions)
- [Python - Distutils Version comparison](https://wiki.python.org/moin/Distutils/VersionComparison)
