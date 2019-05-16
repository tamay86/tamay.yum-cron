Ansible Role: tamay.yumcron
=========

This role installs and configures yumcron.

Requirements
------------

None.

Role Variables
--------------

List of all variables, including default values.

    yum_conf_config:
      update_cmd: default
      update_messages: "yes"
      download_updates: "yes"
      apply_updates: "no"
      random_sleep: 360
      system_name: None
      emit_via: stdio
      output_width: 80
      email_from: root@localhost
      email_to: root
      email_host: localhost
      group_list: None
      group_package_types: "mandatory, default"
      debuglevel: -2
      mdpolicy: "group:main"

Configuration for ```/etc/yum/yum-cron.conf```.

    yum_conf_hourly_config:
      update_cmd: default
      update_messages: "no"
      download_updates: "no"
      apply_updates: "no"
      random_sleep: 15
      system_name: None
      emit_via: stdio
      output_width: 80
      email_from: root
      email_to: root
      email_host: localhost
      group_list: None
      group_package_types: "mandatory, default"
      debuglevel: -2
      mdpolicy: "group:main"

Configuration for ```/etc/yum/yum-cron-hourly.conf```.

Individual values can not be overwritten. You have to always use the whole dictionary in the variable.

Dependencies
------------

None.

Example Playbook
----------------

- install updates daily
- send emails to update@example.com


    ---
    
    - hosts: all
    
      vars:
        yum_conf_config:
          update_cmd: default
          update_messages: "yes"
          download_updates: "yes"
          apply_updates: "yes"
          random_sleep: 360
          system_name: None
          emit_via: stdio
          output_width: 80
          email_from: root@{{ ansible_fqdn }}
          email_to: update@example.com
          email_host: localhost
          group_list: None
          group_package_types: "mandatory, default"
          debuglevel: -2
          mdpolicy: "group:main"
    
      roles:
      - tamay.yumcron

License
-------

MIT

Author Information
------------------

tamay.mueller@gmail.com
