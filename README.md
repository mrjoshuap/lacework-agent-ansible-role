# lacework-agent-ansible-role

Install the Lacework agent on systems using the yum or apt package manager; it will try to fallback to using the install.sh script by default.

## Role Variables

**_Role Configuration_**

* `lacework_skip_import_package_keys` - bool
* `lacework_skip_package_install` - bool
* `lacework_skip_package_repo_install` - bool
* `lacework_skip_install_sh_install` - bool
* `lacework_skip_service_enable` - bool
* `lacework_agent_config_pretty_print` - bool

**_Agent Configuration_**

**_Required_**

* lacework_accessToken

**_Optional_**

* `lacework_accessToken` - string
* `lacework_autoUpgrade` - bool
* `lacework_checkfreq` - string
* `lacework_cmdlinefilter_allow` - comma separated strings (includes wildcards `*` and `?`)
* `lacework_cmdlinefilter_disallow` - comma separated strings (includes wildcards `*` and `?`)
* `lacework_containerRunTime` - string (docker/containerd)
* `lacework_containerEngineEndpoint` - string (path to socket or uri)
* `lacework_cpuLimit` - string
* `lacework_dbSize` - string
* `lacework_fim_filepath` - list
* `lacework_fim_fileignore` - list
* `lacework_fim_runAt` - string time 24hr (HH:MM)
* `lacework_fim_mode` - bool (enable/disable)
* `lacework_fim_noatime` - bool
* `lacework_interfaceConnectionSize` - string
* `lacework_memLimit` - string
* `lacework_perfMode` - string
* `lacework_proxyUrl` - string url
* `lacework_serverurl` - string url
* `lacework_tags` - dictionary

Note: All `lacework_tags` values should be quoted. Booleans will not work unless they are quoted.

**_install.sh_**

* `lacework_install_sh_disable_fim` - bool
* `lacework_install_sh_enable_strict_mode` - bool
* `lacework_install_sh_filter_auditd` - bool

## Dependencies

There are no dependencies for this role.

## Example Playbook

A full example playbook is available in [playbook-example.yml](playbook-example.yml):

    ---

    - name: "Install Lacework Agent"
      hosts: all
      become: yes

      vars:
        lacework_accessToken: "your token"

        lacework_tags:
          foo: "bar"
          test: "var"
          classic: "false"

      roles:
        - mrjoshuap.lacework_agent_ansible_role

## License

MIT
