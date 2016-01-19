# passenger

An ansible galaxy role to install and configure passenger.

## Requirements

You must specify the `passenger_app_path` and will probably want to change the `passenger_user` and `passenger_ruby` to suit.

## Role Variables

* `passenger_app_path` - the directory where the rails or rack app lives
* `passenger_repo_apt_key` - the apt key for the passenger repo
* `passenger_repo` - the passenger repo configuration for apt
* `passenger_user` - username of that will be running passenger and executing the restart command
* `passenger_ruby` - path to the ruby binary

## Dependencies

Requires `ANXS.nginx` role with nginx configured to be built from source, but the `thermistor.passenger` role must be included before it.

You need to add this to the vars for ANXS.nginx, `nginx_source_modules_included` dictionary should look something like:

    nginx_source_modules_included:
      \# <snip> your other ANXS.nginx configured modules here
      passenger_module: "--add-module=/usr/share/passenger/ngx_http_passenger_module"

## Example Playbook

Here is an example configuration:

    - hosts: appservers
      roles:
        - { role: thermistor.passenger, tags: ['passenger'], passenger_app_path: '/srv/www/example.com/example_app', passenger_user: 'deploy' }
        - { role: ANXS.nginx, tags: ['nginx'], nginx_source_version: 1.8.0, monit_protection: false, openssl_version: "1.0.2e" }


## License

Licensed under the MIT License. See the LICENSE file for details.

