# ghost-ansible

Install [Ghost](http://ghost.org) using [Ansible](http://ansibleworks.com),
for an Ubuntu host.

Based on the [setup guide][setup-guide] by @[corbettbarr][corbettbarr]; you'll
end up with:

-   Node.js and NPM installed from ppa:chris-lea/nodejs,
-   A recent (at time of writing) version of Ghost downloaded and extracted,
    -   0.3.0 currently, eventually release.py will detect the latest version,
        or download a Git tag (though that's slightly more involved).
-   Nginx installed from ppa:nginx/stable,
-   Supervisor installed to run Ghost,
-   Nginx, Ghost and Supervisor configured using a few Ansible variables.

## Setup

1.  Assuming the standard Ansible project structure (see
    [ansible-examples][ansible-examples]), clone this repository into
    `roles/ghost`.
2.  Add `ghost` to your roles list in site.yml
3.  Copy and customise the vars in [vars.yml](vars.yml) to your `group_vars`
    or `role_vars` (default file in these directories is
    `(group|role)_vars/all`). Be careful to keep the indentation intact!
4.  Deploy in the usual way (`ansible-playbook -i hosts site.yml`).

## Notes

The release-checker script is hard-coded to `roles/ghost/release.py`, as
`local_action`s operate using the cwd from which you run ansible. This means:

- The clone/submodule of this repo in roles/ needs to be called ghost,
- You need to run ansible from the base directory of your project (where
  roles) is.

[Help me figure this out](http://stackoverflow.com/questions/19389862)


[MIT Licensed](LICENSE.md)

[setup-guide]: http://ghosted.co/install-ghost-digitalocean
[corbettbarr]: http://twitter.com/corbettbarr
[ansible-examples]: https://github.com/ansible/ansible-examples
