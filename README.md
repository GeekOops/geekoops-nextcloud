[![Test deployment](https://github.com/GeekOops/geekoops-nextcloud/actions/workflows/CI.yml/badge.svg)](https://github.com/GeekOops/geekoops-nextcloud/actions/workflows/CI.yml)

# Set up NextCloud

Configurable ansible role for installing nextcloud.
If a redis socket is given, we use that
mysql/mariadb is used for the database.
If you want to use php-fpm with your web-server you have to do it yourself.

- openSUSE Leap 15.4 -> tested

## Role Variables
--------------

You can set the following variables to configure the role. Here listed are the variables and their default settings.


| Value | Description | Default |
|-------|-------------|---------|
|`nc_location` | install location of nextcloud in /srv/www | "htdocs/nextcloud" |
|`nc_data` | data location outside of /srv/www | "ncdata" |
|`nc_db_name` | name of database to utilize | "nextcloud" |
|`nc_db_user` | mysql username | "" |
|`nc_db_pw` | password of mysql user | "" |
|`nc_redis_socket` | redis unix socket to utilize | "" |
|`nc_admin` | In case of a new installation the admin user to create | "Administrator" |
|`nc_admin_pw` | the password of the admin user | "admin_pw" |
|`nc_domain` | The domain of the nextcloud | "cloud.example.org" |
|`nc_sqlbackup` | optional: file with an sql backup | "" |
|`nc_config_php` | optional: file with an exisiting nextcloud config.php | "" |
|`nc_configure_apache_vhost`|Experimental: create an apache vhost file| false |
|`nc_configure_apache_vhost_fpm`| Experimental,optional: php-fpm pool to use in vhost| "/var/run/php-fpm/cloud.sock" |
|`nc_configure_apache_vhost_letsencrypt`| Experimental: letsencrypt certificates to distribute | "/etc/letsencrypt/live/cloud.example.org/" |

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
             nc_redis_socket: "/var/run/redis/cloud.sock"

## Stuff to do afterwards
- If you replayed a backup, you need to copy over plugins, data,...

## issues
- login screen: After pressing login, you are immediatel back at the login screen: ensure tmp folder is accessible: proper right, nc config.php, AND php-fpm ENV variables. (see geekoops-php-fpm)

## License

MIT

# Development
- Test on 15.3
