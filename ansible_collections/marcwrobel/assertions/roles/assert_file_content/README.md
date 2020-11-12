# marcwrobel.assertions.assert_file_content

Assertions on file content.

## Role variables

This role is using the following variables:

- `path` (`path`, required) - the file path.
- `match` (`regex`, required) - the [regex](https://docs.python.org/3.7/howto/regex.html) to test against the file content.
- `ignorecase` (`boolean`, required, default=`true`) - whether the match must ignore case.
- `multiline` (`boolean`, required, default=`true`) - whether the match must be multi-line.

## Usage

    - name: 'Assert that /etc/passwd contains root'
      include_role:
        name: 'assert_file_content'
      vars:
        path: '/path/to/file'
        match: '$root:'

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - Tests – Testing strings](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#testing-strings)
- [Python - Regular Expression HOWTO](https://docs.python.org/3.7/howto/regex.html)
