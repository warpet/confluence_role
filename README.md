![Logo](logo.gif)

[![Build Status](https://travis-ci.org/idealista/confluence_role.png)](https://travis-ci.org/idealista/confluence_role)

Confluence Ansible role
=========

This role installs a standalone Confluence server

- [Getting Started](#getting-started)
	- [Prerequisites](#prerequisites)
	- [Installing](#installing)
- [Usage](#usage)
- [Testing](#testing)
- [Built With](#built-with)
- [Versioning](#versioning)
- [Authors](#authors)
- [License](#license)
- [Contributing](#contributing)

## Getting started

Install Confluence in a Debian system. Optionally, it can install external jdbc driver and prepare confluence to run behind a proxy server

### Prerequisities

Ansible 2.9.9 version installed.

Molecule 3.x.x version installed.

For testing purposes, [Molecule](https://molecule.readthedocs.io/) with [Docker](https://www.docker.com/) as driver and [Goss](https://github.com/aelsabbahy/goss) as verifier.

Also, it requires Java installed, you can use [Ansible Galaxy - Idealista.Java_role](https://galaxy.ansible.com/idealista/java_role)


### Installing

Create or add to your roles dependency file (e.g requirements.yml):

``` yml
- src: idealista.confluence_role
  version: 1.0.0
  name: confluence
```

Install the role with ansible-galaxy command:

```
ansible-galaxy install -p roles -r requirements.yml -f
```

Use in a playbook:

```
- hosts: someserver
  roles:
    - role: confluence
```

## Usage

Variables explanation:

- `confluence_tmp_dir` temporary directory
- `confluence_pkg_version` this is the confluence version to install
- `confluence_pkg_download_url` use this variable to change download url
- `confluence_user` this is the owner for all generated files
- `confluence_group` this is the group for all generated files
- `confluence_home_path` this is the path where confluence will be installed
- `confluence_data_path` this is the path where confluence store data files
- `confluence_logs_path` this is the path where confluence logs will be stored
- `confluence_server_port` this is the port where confluence is listening on
- `confluence_connector_port` this is used by confluence as connector port
- `confluence_context` use this variable to define a url context, for example, 'http://example:8090/confluence' if not, leave it empty
- `confluence_proxy_enabled` use this variable if you want use confluence behind a proxy server
- `confluence_jdbc_install` enables external jdbc driver installation
- `confluence_system_dependencies` packages required to install a virtualenv
- `confluence_java_opts.xms` java xms value
- `confluence_java_opts.xmx` java xmx value
- `confluence_catalina_opts` use this variable to override catalina parameters
- `confluence_logrotate_enabled` activate logrotate config
- `confluence_logrotate_config_file` logrotate config location

Optional variables:

- `confluence_jdbc_origin` allow jdbc driver installation from maven or direct download. Valid values _'url'_ or _'maven'_
- `confluence_jdbc_download_url` this is the url to download jdbc driver

    If you use maven as origin repository define these variables
- `confluence_jdbc_maven.artifact_id`
- `confluence_jdbc_maven.group_id`
- `confluence_jdbc_maven.version` 
- `confluence_jdbc_maven.repo_url`

    Use this variables to config confluence behind a proxy server
- `confluence_proxy.public_port` sets the public port
- `confluence_proxy.public_domain` sets the public domain
- `confluence_proxy.secure` uses HTTPS reverse proxy if true, otherwise HTTP.
- `confluence_proxy.additionalParameters` sets additional parameters of connector
    configuration.
    For example relaxedPathChars/relaxedQueryChars as documented in https://confluence.atlassian.com/kb/samplehttpconnector-753893891.html

# Testing

### Install dependencies

```sh
$ pipenv sync
```

For more information read the [pipenv docs](ipenv-fork.readthedocs.io/en/latest/).

### Testing

```sh
$ pipenv run molecule test 
```

## Built With

![Ansible](https://img.shields.io/badge/ansible-2.8.0-green.svg)

## Versioning

For the versions available, see the [tags on this repository](https://github.com/idealista/jira_role/tags).

Additionaly you can see what change in each version in the [CHANGELOG.md](CHANGELOG.md) file.

## Authors

* **Idealista** - *Work with* - [idealista](https://github.com/idealista)

See also the list of [contributors](https://github.com/idealista/confluence_role/contributors) who participated in this project.

## License

![Apache 2.0 License](https://img.shields.io/hexpm/l/plug.svg)

This project is licensed under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license - see the [LICENSE](LICENSE) file for details.

## Contributing

Please read [CONTRIBUTING.md](.github/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

