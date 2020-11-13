## Requirements

The following instructions assume you have Python 3 installed along with [`python-pip`](https://pip.pypa.io/en/stable/), [`python-venv`](https://docs.python.org/3/library/venv.html)
[`python-wheel`](https://pythonwheels.com/) and `libssl-dev` (for Molecule).

For instance on Debian 10 :

    sudo apt install python3-pip python3-venv python3-wheel libssl-dev

[Docker](https://www.docker.com/) must also be installed to run the tests. Have a look at the [official documentation](https://docs.docker.com/engine/install/debian/)
for installation instructions.

## Prepare development environment

This project needs [Ansible](https://www.ansible.com/), [YAMLlint](https://yamllint.readthedocs.io/en/stable/), [Ansible-lint](https://github.com/ansible/ansible-lint)
and [Molecule](https://molecule.readthedocs.io/en/stable/).

The best and easiest way to install those dependencies is to use the `requirements.txt` in a Python [virtual environment](https://docs.python.org/3/library/venv.html).

    python3 -m venv .environments/ansible
    source .environments/ansible/bin/activate
    pip install -r requirements.txt

    ansible --version
    yamllint --version
    ansible-lint --version
    molecule --version

## Run linting

Linting is performed using YAMLlint and Ansible-lint :

    yamllint .
    ansible-lint

## Run integration tests

### Run integration tests on a single distribution

Integration tests are executed by Molecule using [Jeff Geerling's](https://www.jeffgeerling.com/) Docker images. Any `docker-xxx-ansible` images listed on his
profile on [Docker Hub](https://hub.docker.com/u/geerlingguy/) can be used with the `xxx` identifier passed as the `MOLECULE_DISTRO` environment variable. For
instance, to run the integration tests on CentOS 8:

    cd ansible_collections/marcwrobel/assertions
    MOLECULE_DISTRO=centos8 molecule test

The default distribution is `debian10`.

### Run integration tests on multiple distributions

If you want to launch integration tests on multiple distributions :

    cd ansible_collections/marcwrobel/assertions
    for distro in debian10 ubuntu2004 centos8 fedora33 amazonlinux2; do
        MOLECULE_DISTRO=$distro molecule test
    done

### Run integration tests during the development lifecycle

During the development lifecycle you may prefer to keep the docker containers running and run `molecule` commands individually:

    # Creates and configures instances
    molecule converge

    # Runs automated tests against instances
    molecule verify

    # Runs the converge step a second time and check that no tasks are marked as changed
    molecule idempotence

## Continuous integration

The GitHub Action workflow [`CI`](https://github.com/marcwrobel/ansible-collection-assertions/actions?query=workflow%3ACI) is executed for each commit, on merge
request (targeting the `main` branch) and at least once a week on saturday morning. This workflow runs :

- linting with YAMLlint and Ansible-lint,
- integration tests on collections with Molecule.

## Release

In order to publish a new release on [Ansible Galaxy](http://galaxy.ansible.com/) follow this process:

0. Run `source .environments/ansible/bin/activate` to switch to Ansible 2.10+ (the minimum required version).
1. Update `galaxy.yml` manually, making sure the `version` key has the correct version.
2. Push all changes, make sure tests are passing.
3. Tag a new release (e.g. `x.y.z`), and push it to GitHub.
4. Run `ansible-galaxy collection build` to build the release artifact (a `marcwrobel-assertions-x.y.z.tar.gz` file) from the collection directory.
5. Make sure the file `~/.ansible/galaxy_token` has the correct Ansible Galaxy token (for authentication).
6. Run `ansible-galaxy collection publish ./marcwrobel-assertions-x.y.z.tar.gz` from the collection directory.

See also : https://www.jeffgeerling.com/blog/2020/automatically-building-and-publishing-ansible-galaxy-collections.
