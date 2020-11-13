# marcwrobel.assertions.assert_that_file

Assertions on file content (`has_content_matching`).

If you are looking for mode, owner or group assertions, take a look at `marcwrobel.assertions.assert_that_path`.

## Role variables

This role is using the following variables:

- `path` (`path`, required) - the file path.
- `has_content_matching` (`regex`, optional) - the [regex](https://docs.python.org/3.7/howto/regex.html) to test against the file content.
- `ignorecase_for_content_matching` (`boolean`, required, default=`true`) - whether the match must ignore case during `has_content_matching` assertion.
- `multiline_for_content_matching` (`boolean`, required, default=`true`) - whether the match must be multi-line during `has_content_matching` assertion.

## Usage

    - name: 'Assert that /tmp/test is managed by Ansible'
      include_role:
        name: 'assert_that_file'
      vars:
        path: '/path/to/file'
        has_content_matching: '^# Ansible managed'

    - name: 'Assert that /tmp/toto match the given multiline string'
      include_role:
        name: 'assert_that_file'
      vars:
        path: '/path/to/file'
        has_content_matching: 'line1\n.+\nline3'
        multiline_for_content_matching: false

    - name: 'Assert that /tmp/toto match the given case-sensitive string'
      include_role:
        name: 'assert_that_file'
      vars:
        path: '/path/to/file'
        has_content_matching: 'Case-sensitive string.'
        ignorecase_for_content_matching: false

    # This is allowed, but do nothing
    - name: 'Assert nothing'
      vars:
        path: '/path/to/file'
      include_role:
        name: 'assert_that_file'

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - Tests – Testing strings](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#testing-strings)
- [Python - Regular Expression HOWTO](https://docs.python.org/3.7/howto/regex.html)
