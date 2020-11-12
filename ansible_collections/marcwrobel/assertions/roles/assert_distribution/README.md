# marcwrobel.assertions.assert_distribution

Assertions on the current distribution version: name, version.

## Role variables

This role is using the following variables:

- `is_in` (`string[]`, optional) - the list of the allowed distributions. An item in the `is_in` can be:
  - Only the distribution name if you want to match all distribution's versions : `Debian`, `CentOS`, `RedHat`, `Ubuntu`, `Fedora`, `Amazon`...
  - The distribution name with its major version if you want to match all distribution's versions for this major version : `Debian 10`, `CentOS 8`...
  - The distribution name with its full version if you want to match a specific distribution's versions : `Ubuntu 20.04`, `CentOS 8.2`...

Names and versions comes from the special Ansible variables `ansible_distribution`, `ansible_distribution_major_version` and `ansible_distribution_version`.
Note that [point release number](https://wikipedia.org/wiki/Point_release) is rarely included in `ansible_distribution_version`. As of 2020-11-13:
- Ubuntu 20.04: `{ ansible_distribution: "Ubuntu", ansible_distribution_major_version: "20", ansible_distribution_version: "20.04" }`
- Debian 10: `{ ansible_distribution: "Debian", ansible_distribution_major_version: "10", ansible_distribution_version: "10" }`
- Amazon Linux 2: `{ ansible_distribution: "Amazon", ansible_distribution_major_version: "2", ansible_distribution_version: "2" }`
- CentOS 8: `{ ansible_distribution: "CentOS", ansible_distribution_major_version: "8", ansible_distribution_version: "8.2" }`
- Fedora 33: `{ ansible_distribution: "Fedora", ansible_distribution_major_version: "33", ansible_distribution_version: "33" }`

## Usage

    - name: 'Assert that the distribution is supported'
      include_role:
        name: 'assert_distribution'
      vars:
        is_in: [ 'Debian 10', 'CentOS 8' ]

## Requirements

None.

## Dependencies

None.

## Implementation notes

This role does not implement the version check like `marcwrobel.assertions.assert_ansible` because :
- it was too complex to include `min` and `max` variables for multiple distributions,
- point release are not frequent and point release number is rarely included in `ansible_distribution_version`, making it less relevant.

## Links

- [Ansible - Discovering variables: facts and magic variables - Ansible facts](https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html#ansible-facts)
