# Ansible Role: Apache Tomcat

[![CI](https://github.com/silviuvulcan/ansible-role-tomcat/workflows/CI/badge.svg?event=push)](https://github.com/silviuvulcan/ansible-role-tomcat/actions?query=workflow%3ACI)

Sets up Apache Tomcat from binary tgz.

## Requirements

None.

## Role Variables

See `defaults/main.yml`:

    tomcat_force_install: false

Force installation even if target folder already exists

    tomcat_user: tomcat
    tomcat_group: tomcat

User to deploy and run under

    tomcat_drivers: 
      - https://example.com/somedriver-v1.0.jar

Download drivers to `lib/`

## Dependencies

None.

## Example Playbook

```yaml
---
- hosts: all
  hosts: all
  become: yes

  roles:
    - role: filviu.tomcat
      tomcat_version: 9.0.27
      tomcat_install_path: /opt
      tomcat_user: tomcat
      tomcat_group: tomcat
      tomcat_drivers:
        - https://jdbc.postgresql.org/download/postgresql-9.4-1206-jdbc4.jar
# tomcat_users you might be using in the tomcat-users.xml.j2 template
      tomcat_users:
        someuser:
          password: "some_encrypted_password"
          roles: "ROLE1, ROLE2"
      tomcat_server_xml_template: tomcat/server.xml.j2
      tomcat_users_xml_template: tomcat/tomcat-users.xml.j2
      #tomcat_setenv_sh_template: tomcat/setenv.sh.j2
```

## License

MIT / BSD

## Author Information

This role was created by Silviu Vulcan to scratch his own itch.
