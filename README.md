bvansomeren.periodic-conf
=========================

Sets up your /etc/periodic.conf to override the /etc/defaults/periodic.conf values for periodic maintenance tasks in FreeBSD.  
You will find more information on how to configure periodic.conf in it's manpage.

Requirements
------------

It's in base, use the platform, Luke.

Role Variables
--------------

Basically everything that's in periodic should be supported. If you try to add something that shouldn't exist the role will fail.
Check the defaults/main.yml for a list of allowed names.

```
 periodic_conf: []
```

**periodic\_conf** contains a name/value list with entries for periodic.conf. See example Playbook for an idea how to use this properly.  


Dependencies
------------

None

Example Playbook
----------------


```
    - hosts: servers
      roles:
      - bvansomeren.periodic-conf
      vars:
      - periodic_conf:
        - { name: "daily_output", value: "root" }
        - { name: "daily_clean_tmps_enable", value: "YES" }
        - { name: "daily_scrub_zfs_enable", value: "YES" }
        - { name: "daily_scrub_zfs_pools", value: "zroot" }
        - { name: "daily_scrub_zfs_default_threshold", value: "14" }
        - { name: "daily_status_zfs_enable", value: "YES" }
        - { name: "daily_status_zfs_zpool_list_enable", value: "YES" }
```

see **man periodic.conf** For more information on periodic.conf

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
