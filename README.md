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
|`drupal_location` | install location of drupal in /srv/www | "drupal9-hp" |
|`drupal_db_name` | Who gets update notifications | "" |
|`drupal_db_user` | Who gets update notifications | "" |
|`drupal_dp_pw` | Who gets update notifications | "" |
|`drupal_trusted_host_pattern` | Who gets update notifications | "" |

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: jellyfish
      roles:
         - { role: geekoops-nextcloud, letsencrypt_domains: "www.example.org", letsencrypt_mail_address: "webmaster@example.org" }

An advanced example for the imaginary `jellyfish` test server

    - hosts: jellyfish
      roles:
         - role: geekoops-nextcloud
           vars:
             letsencrypt_mail_address: "webmaster@example.org"
             letsencrypt_domains:
               - "www.example.org"
               - "smtp.example.org"
               - "imap.example.org"

## Stuff to do afterwards
- If you replayed a backup, you need to copy over plugins, data

## License

MIT

# Development
- Test on 15.3
