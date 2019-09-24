resolv_conf
===========

Ansible role which helps to configure `resolv.conf` file.

The configuration of the role is done in such way that it should not be necessary
to change the role for any kind of configuration. All can be done either by
changing role parameters or by declaring completely new configuration as a
variable. That makes this role absolutely universal. See the examples below for
more details.

Please report any issues or send PR.


Example
-------

```yaml
---

# Example of how to use the default settings
- hosts: myhost
  roles:
    - resolv_conf

# Example how to customize some of the settings
- hosts: myhost
  roles:
    - role: resolv_conf
      # Custom DNS servers
      resolv_conf_nameserver:
        - dns1.example.com
        - dns2.example.com
      # Custom search list
      resolv_conf_search:
        - example.com
        - sub.example.com
```


Role variables
--------------

List of variables used by the role:

```yaml
# Default location of the resolv.conf
resolv_conf_file: /etc/resolv.conf

# Default nameservers
resolv_conf_nameserver:
  - 8.8.8.8
  - 8.8.4.4

# Default domain
resolv_conf_domain: ''

# Default search list
resolv_conf_search: []

# Defautl sort list
resolv_conf_sortlist: []

# Default options
resolv_conf_options: []
```


Notes
-----

In order to prevent `resolv.conf` being changed by DHCP, set `PEERDNS=no` in your
`network-scripts` on RedHat or `SET_DNS='no'` in `/etc/default/dhcpcd` on Debian.


License
-------

MIT


Author
------

Jiri Tyr
