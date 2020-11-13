# marcwrobel.assertions.assert_that_file

Assertions on file content (`has_content_matching`).

If you are looking for mode, owner or group assertions, take a look at `marcwrobel.assertions.assert_path`.

## Role variables

This role is using the following variables:

- `path` (`path`, required) - the file path.
- `has_content_matching` (`regex`, required) - the [regex](https://docs.python.org/3.7/howto/regex.html) to test against the file content.
- `ignorecase_for_content_matching` (`boolean`, required, default=`true`) - whether the match must ignore case during `has_content_matching` assertion.
- `multiline_for_content_matching` (`boolean`, required, default=`true`) - whether the match must be multi-line during `has_content_matching` assertion.

## Usage

    - name: 'Assert that /tmp/test is managed by Ansible'
      include_role:
        name: 'assert_that_file'
      vars:
        path: '/path/to/file'
        has_content_matching: '^# Ansible managed'

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - Tests – Testing strings](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#testing-strings)
- [Python - Regular Expression HOWTO](https://docs.python.org/3.7/howto/regex.html)
