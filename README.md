# passenger

An ansible galaxy role to install and configure passenger.

## Requirements

You must specify:
* `passenger_app_path`

You will probably want to change:
* `passenger_user`
* `passenger_ruby`

## Role Variables

* `passenger_app_path` - the directory where the rails or rack app lives
* `passenger_repo_apt_key` - the apt key for the passenger repo
* `passenger_repo` - the passenger repo configuration for apt
* `passenger_user` - username of that will be running passenger and executing the restart command, default is `deploy`
* `passenger_ruby` - path to the ruby binary, default is `/usr/local/bin/ruby`
* `passenger_pre_start_url` - used to pre start the app if present
* `passenger_max_pool_size` - default is 3
* `passenger_min_instances` - default is 3

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

