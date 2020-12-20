# marcwrobel.assertions.assert_that_file

Assertions on file content (`exists`, `has_mode`, `has_owner`, `has_group`, `has_content_matching`).

## Role variables

This role is using the following variables:

- `with_path` (`path`, required) - the file path.
- `exists` (`boolean`, required, default=`true`) - whether the path exists.
- `has_mode` (`string`, optional) - expected mode in octal representation (e.g. `0644`) of the path, if it exists. Mode must be .
- `has_owner` (`string`, optional) - expected owner name (not uid) of the path, if it exists.
- `has_group` (`string`, optional) - expected group name (not guid) of the path, if it exists.
- `has_content_matching` (`regex`, optional) - the [regex](https://docs.python.org/3.7/howto/regex.html) to test against the file content.
- `using_ignorecase_for_content_matching` (`boolean`, required, default=`true`) - whether the match must ignore case during `has_content_matching` assertion.
- `using_multiline_for_content_matching` (`boolean`, required, default=`true`) - whether the match must be multi-line during `has_content_matching` assertion.

## Usage

```yaml
- name: 'Assert that /path/to/file exists, is a file, have mode 0640 and belongs to root:root'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    with_path: '/path/to/file'
    has_mode: '0640'
    has_owner: 'root'
    has_group: 'root'

- name: 'Assert that /path/to/file exists'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    with_path: '/path/to/file'

- name: 'Assert that /path/to/file does not exist'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    with_path: '/path/to/file'
    exists: false

- name: 'Assert that /tmp/test is managed by Ansible'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    with_path: '/path/to/file'
    has_content_matching: '^# Ansible managed'

- name: 'Assert that /tmp/toto match the given multiline string'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    with_path: '/path/to/file'
    has_content_matching: 'line1\n.+\nline3'
    using_multiline_for_content_matching: false

- name: 'Assert that /tmp/toto match the given case-sensitive string'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
  vars:
    with_path: '/path/to/file'
    has_content_matching: 'Case-sensitive string.'
    using_ignorecase_for_content_matching: false

# This is allowed, but do nothing
- name: 'Assert nothing'
  vars:
    with_path: '/path/to/file'
  include_role:
    name: 'marcwrobel.assertions.assert_that_file'
```

## Requirements

None.

## Dependencies

None.

## Links

- [Ansible - Tests – Testing strings](https://docs.ansible.com/ansible/latest/user_guide/playbooks_tests.html#testing-strings)
- [Python - Regular Expression HOWTO](https://docs.python.org/3.7/howto/regex.html)
