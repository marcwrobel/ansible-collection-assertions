# marcwrobel.assertions.assert_that_distribution

Assertions on distributions (`is_in`).

## Role variables

This role is using the following variables:

- `is_in` (`string[]`, optional) - the list of the allowed distributions. Items in this list can be:
  - The distribution name only, if you want to match all distribution's versions (`Debian`, `CentOS`, `RedHat`, `Ubuntu`, `Fedora`, `Amazon`...),
  - or the distribution name with its major version, if you want to match all distribution's versions for this major version (`Debian 10`, `CentOS 8`...),
  - or the distribution name with its full version, if you want to match a specific distribution's versions (`Ubuntu 20.04`, `CentOS 8.2`...).

Names and versions come from the Ansible facts `ansible_distribution`, `ansible_distribution_major_version` and `ansible_distribution_version`. Note that [point
release number](https://wikipedia.org/wiki/Point_release) is rarely included in `ansible_distribution_version`. As of 2020-11-13:

- Ubuntu 20.04: `{ ansible_distribution: "Ubuntu", ansible_distribution_major_version: "20", ansible_distribution_version: "20.04" }`
- Debian 10: `{ ansible_distribution: "Debian", ansible_distribution_major_version: "10", ansible_distribution_version: "10" }`
- Amazon Linux 2: `{ ansible_distribution: "Amazon", ansible_distribution_major_version: "2", ansible_distribution_version: "2" }`
- CentOS 8: `{ ansible_distribution: "CentOS", ansible_distribution_major_version: "8", ansible_distribution_version: "8.2" }`
- Fedora 33: `{ ansible_distribution: "Fedora", ansible_distribution_major_version: "33", ansible_distribution_version: "33" }`

## Usage

    - name: 'Assert that the distribution is supported'
      include_role:
        name: 'assert_that_distribution'
      vars:
        is_in: [ 'Debian', 'RedHat 8', `Ubuntu 20.04` ]

    # This is allowed, but always fails
    - name: 'Assert nothing'
      include_role:
        name: 'assert_that_distribution'
      vars:
        is_in: [ ]

    # This is allowed, but do nothing
    - name: 'Assert nothing'
      include_role:
        name: 'assert_that_distribution'

## Requirements

None.

## Dependencies

None.

## Implementation notes

This role does not implement the version check like `marcwrobel.assertions.assert_that_ansible` because :
- it was too complex to include `min` and `max` variables for multiple distributions,
- point release are not frequent and point release number is rarely included in `ansible_distribution_version`, making it less relevant.

## Links

- [Ansible - Discovering variables: facts and magic variables - Ansible facts](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#ansible-facts)
