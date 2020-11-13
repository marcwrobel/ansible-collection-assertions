# marcwrobel.assertions.assert_that_service

Assertions on services (`exists`, `has_state`, `has_status`).

## Role variables

This role is using the following variables:

- `name` (`string`, required) - the service name.
- `exists` (`boolean`, required, default=`true`) - whether the service exists.
- `has_state` (`running | stopped | unknown`, optional) - the expected service state.
- `has_status` (`enabled | disabled | static | indirect | unknown`, optional) - the expected service status.

## Usage

    - name: 'Assert that firewalld.service exists, is running and is enabled'
      include_role:
        name: 'marcwrobel.assertions.assert_that_service'
      vars:
        name: 'firewalld.service'
        has_state: 'running'
        has_status: 'enabled'

    - name: 'Assert that firewalld.service exists'
      include_role:
        name: 'marcwrobel.assertions.assert_that_service'
      vars:
        name: 'firewalld.service'

    - name: 'Assert that firewalld.service does not exist'
      include_role:
        name: 'marcwrobel.assertions.assert_that_service'
      vars:
        name: 'firewalld.service'
        exists: false

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - ansible.builtin.service_facts – Return service state information as fact data](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/service_facts_module.html)
