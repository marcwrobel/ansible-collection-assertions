# marcwrobel.assertions.assert_path

Assertions for paths : existence, type, mode, owner, group.

## Role variables

This role is using the following variables:

- `path` (`path`, required) - the path to test.
- `exists` (`boolean`, default=`true`) - whether the path exists.
- `type` (`string`, optional) - expected type of the path, if it exists. Supported types are :
  - `file`: path is a regular file
  - `directory`: path is a directory
  - `link`: path is a symbolic link
- `mode` (`string`, optional) - expected mode in octal representation (e.g. `0644`) of the path, if it exists. Mode must be .
- `owner` (`string`, optional) - expected owner name (not uid) of the path, if it exists.
- `group` (`string`, optional) - expected group name (not guid) of the path, if it exists.

## Usage

    - name: 'Assert that /path/to/file exists, is a file, have mode 0640 and belongs to root:root'
      include_role:
        name: 'assert_path'
      vars:
        path: '/path/to/file'
        type: 'file'
        mode: '0640'
        owner: 'root'
        group: 'root'

    - name: 'Assert that /path/to/file does not exist'
      include_role:
        name: 'assert_path'
      vars:
        path: '/path/to/file'
        exists: false

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - ansible.builtin.stat – Retrieve file or file system status](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/stat_module.html)
