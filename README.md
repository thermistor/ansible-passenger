# passenger

An ansible galaxy role to install and configure passenger.

## Requirements

TBD

## Role Variables

* `passenger_repo_apt_key` - the apt key for the passenger repo
* `passenger_repo` - the passenger repo configuration for apt
* `passenger_user` - username of that will be running passenger and executing the restart command
* `passenger_ruby` - path to the ruby binary

## Dependencies

Requires `ANXS.nginx` role.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: appservers
      roles:
        - { role: passenger, tags: ['passenger'], passenger_user: 'deploy' }

## License

Licensed under the MIT License. See the LICENSE file for details.

