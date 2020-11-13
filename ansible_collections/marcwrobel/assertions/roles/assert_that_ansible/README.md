# marcwrobel.assertions.assert_that_ansible

Assertions on [Ansible](https://www.ansible.com/) (`has_min_version`, `has_max_version`).

## Role variables

This role is using the following variables:

- `has_min_version` (`string`, optional) - the minimum required Ansible version, included (`has_min_version >= ansible_version.full`).
- `has_max_version` (`string`, optional) - the maximum required Ansible version, excluded (`ansible_version.full < has_max_version`).
- `strict_version_parsing` (`boolean`, required, default=`false`) - whether [strict version parsing](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions))
  must be used.

## Usage

    - name: 'Assert that Ansible version is >= 2.8 and < 2.10'
      include_role:
        name: 'marcwrobel.assertions.assert_that_ansible'
      vars:
        has_min_version: '2.8'
        has_max_version: '2.10'

    - name: 'Assert that Ansible version is >= 2.8'
      include_role:
        name: 'marcwrobel.assertions.assert_that_ansible'
      vars:
        has_min_version: '2.8'

    - name: 'Assert that Ansible version is < 2.10'
      include_role:
        name: 'marcwrobel.assertions.assert_that_ansible'
      vars:
        has_max_version: '2.10'

    - name: 'Assert that Ansible version is >= 2.8 and < 2.10 with strict version parsing'
      include_role:
        name: 'marcwrobel.assertions.assert_that_ansible'
      vars:
        has_min_version: '2.8'
        has_max_version: '2.10'
        strict_version_parsing: true

    # This is allowed, but do nothing
    - name: 'Assert nothing'
      include_role:
        name: 'marcwrobel.assertions.assert_that_ansible'

## Requirements

None.

## Dependencies

None.

## Implementation notes

### Why `has_max_version` is excluded from comparison ?

`has_max_version` is excluded from comparison to support the most common use case with versions comparison : supporting a version with its fixes up to a given
version without knowing the latest fix version.

### Versions comparison
This role is using the [`version` test](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions) internally : versions
comparison respects the `version` test specification.

## Links

- [Ansible - Discovering variables: facts and magic variables - Ansible version](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#ansible-version)
- [Ansible - Tests - Comparing versions](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#comparing-versions)
- [Python - Distutils Version comparison](https://wiki.python.org/moin/Distutils/VersionComparison)
