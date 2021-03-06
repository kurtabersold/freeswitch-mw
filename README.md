Freeswitch
==========

[![Build Status](https://travis-ci.org/kurtabersold/freeswitch-mw.svg?branch=master)](https://travis-ci.org/kurtabersold/freeswitch-mw)

Ansible role for FreeSwitch

Requirements
------------

- Tested on Ansible 1.8 or higher.

Role Variables
--------------

The role variables and default values.


    freeswitch_version: v1.6 #FreeSwitch version. Becareful, only tested with 1.6 version for the time being
    freeswitch_sources_path: /usr/src/freeswitch #Path to the FreeSwitch source directory
    freeswitch_path: /usr/local/freeswitch #Path to the FreeSwith directory
    freeswitch_owner: freeswitch
    freeswitch_group: daemon
    freeswitch_modules_template: ../templates/modules/modules.conf #modules.conf file used for FreeSwitch compilation
    freeswitch_init_template: ../templates/freeswitch-systemd.freeswitch.service # systemd unit file template
    freeswitch_daemon_args: -nonat # -ncwait is set in systemd unit file
    freeswitch_configure_command: configure # freeswicth configure command - you can add option
    freeswitch_log_rotate_script: ../templates/freeswitch_log_rotation # log management script
    freeswitch_log_conf_template: ../template/logfile.conf.xml # freeswitch log configuration file template
    fail2ban_conf: ../templates/fail2ban/fail2ban.conf.xml # Module configuration file
    fail2ban_jail: ../templates/fail2ban/freeswitch.jail # fail2ban template jail for FreeSwitch
    fail2ban_filter: ../templates/fail2ban/freeswitch.filter # Fail2ban filter template for FreeSwitch


Dependencies
------------



Example Playbook
----------------

    - hosts: all
	  vars_files:
	    - 'defaults/main.yml'
	  tasks:
	    - include: 'tasks/main.yml'
	  handlers:
	    - include: 'handlers/main.yml'

License
-------

Licensed under the GPL v3 license. See the LICENSE file for details.

Author Information
------------------

Mathias WOLFF [Blog des télécoms](http://www.blog-des-telecoms.com) - [PyFreeBilling](https://www.pyfreebilling.com)
