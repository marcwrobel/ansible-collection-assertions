# marcwrobel.assertions.assert_that_path

Assertions for paths (`exists`, `has_type`, `has_mode`, `has_owner`, `has_group`).

## Role variables

This role is using the following variables:

- `path` (`path`, required) - the path to test.
- `exists` (`boolean`, required, default=`true`) - whether the path exists.
- `has_type` (`file | directory | link`, optional) - expected type of the path, if it exists. Supported types are :
- `has_mode` (`string`, optional) - expected mode in octal representation (e.g. `0644`) of the path, if it exists. Mode must be .
- `has_owner` (`string`, optional) - expected owner name (not uid) of the path, if it exists.
- `has_group` (`string`, optional) - expected group name (not guid) of the path, if it exists.

## Usage

    - name: 'Assert that /path/to/file exists, is a file, have mode 0640 and belongs to root:root'
      include_role:
        name: 'marcwrobel.assertions.assert_that_path'
      vars:
        path: '/path/to/file'
        has_type: 'file'
        has_mode: '0640'
        has_owner: 'root'
        has_group: 'root'

    - name: 'Assert that /path/to/file exists'
      include_role:
        name: 'marcwrobel.assertions.assert_that_path'
      vars:
        path: '/path/to/file'

    - name: 'Assert that /path/to/file does not exist'
      include_role:
        name: 'marcwrobel.assertions.assert_that_path'
      vars:
        path: '/path/to/file'
        exists: false

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - ansible.builtin.stat – Retrieve file or file system status](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/stat_module.html)
