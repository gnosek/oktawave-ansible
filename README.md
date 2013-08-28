Oktawave Ansible plugin
=======================

Installation
------------

    git clone https://github.com/gnosek/oktawave-ansible.git
    pip install git+https://github.com/gnosek/oktawave-cli.git
    ln -s oktawave /your/playbook/dir/library/oktawave

Usage
-----

See example playbooks. Supported parameters:

 - `okta_username`, `okta_password` -- Oktawave account credentials
 - `name` -- OCI name
 - `state` -- `present` or `absent`, desired OCI state (creates/deletes) OCI to match
 - `origin_oci` -- OCI ID to clone from
 - `template_id` -- OCI template ID
 - `oci_class` -- optional OCI class (Mini, Starter, etc.)
 - `change_at_midnight` (`yes`/`no`) -- defer change until midnight to avoid immediate reboot
 - `wait_timeout` -- how long to wait (in seconds, default 300) for new OCI to appear before reporting an error

Return value contains quite a lot of OCI settings/state info, run the example playbooks with `-vvv` to see it.

Supported operations
--------------------

### Creating an OCI from a template

Required parameters: `name`, `template_id`
Optional parameters: `oci_class` (defaults to template default)

XXX: no support for fetching password of new instance

### Cloning an OCI from another one

Required parameters: `name`, `origin_oci`

### Removing an OCI

Just say `state=absent`

Required parameters: `name`

### Changing OCI class

Required parameters: `name`, `oci_class`
