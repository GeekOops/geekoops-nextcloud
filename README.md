[![Test deployment](https://github.com/GeekOops/geekoops-nextcloud/actions/workflows/CI.yml/badge.svg)](https://github.com/GeekOops/geekoops-nextcloud/actions/workflows/CI.yml)

# Set up NextCloud

Configurable ansible role for installing nextcloud.
If php-fpm is present we configure nextcloud to use it.
If a redis socket is given, we use that
mysql/mariadb is used for the database.

- openSUSE Leap 15.4 -> tested

## Role Variables
--------------

You can set the following variables to configure the role. Here listed are the variables and their default settings.


| Value | Description | Default |
|-------|-------------|---------|
|`sqlbackup` | file with an sql backup | "" |
|`nc_location` | install location of nextcloud in /srv/www | "nextcloud" |
|`nc_data` | data location outside of /srv/www | "ncdata" |
|`nc_db_name` | name of database to utilize | "nextcloud" |
|`nc_db_user` | mysql username | "" |
|`nc_db_pw` | password of mysql user | "" |
|`nc_redis_socket` | redis unix socket to utilize | "" |
|`nc_php_fpm_pool` | name of the PHP-fpm pool to utilize | "" |
|`drupal_trusted_host_pattern` | Who gets update notifications | "" |

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: jellyfish
      roles:
         - { role: geekoops-nextcloud, nc_db_pw: "1234bcd" }

An advanced example for the imaginary `jellyfish` test server

    - hosts: jellyfish
      roles:
         - role: geekoops-nextcloud
           vars:
             nc_db_pw: "1234abcd"
             nc_php_fpm_pool: "cloud"

## Stuff to do afterwards
- If you replayed a backup, you need to copy over plugins, data

## License

MIT

# Development
- Test on 15.3
