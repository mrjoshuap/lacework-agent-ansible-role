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
* `lacework_cmdlinefilter_disallow` - command separated string
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

An example playbook is available in the [playbook-example.yml](playbook-example.yml):

    ---

    - name: "Install Lacework Agent"
      hosts: jumphost.local
      become: yes

      vars:
        lacework_accessToken: "your token"

        # defaults file for lacework-agent-ansible-role
        # lacework_skip_import_package_keys: yes
        # lacework_skip_package_install: yes
        # lacework_skip_package_repo_install: yes
        # lacework_skip_install_sh_install: no
        # lacework_skip_service_enable: yes
        # lacework_agent_config_pretty_print: yes

        # lacework_autoUpgrade: "enable"
        # lacework_checkfreq: "60m"
        # lacework_cmdlinefilter_allow: "*"
        # lacework_cmdlinefilter_disallow: ""

        # Docker
        # lacework_containerRunTime: "docker"
        # lacework_containerEngineEndpoint: "unix:///var/run/docker.sock"

        # Containerd
        # lacework_containerRunTime: "containerd"
        # lacework_containerEngineEndpoint: "unix:///run/containerd/containerd.sock"

        # lacework_cpuLimit: "500m"
        # lacework_dbSize: "2G"
        # lacework_fim_filepath:
        #   - "/home/user/.ssh"
        #   - "/opt/bin"
        # lacework_fim_fileignore:
        #   - "/etc/fstab"
        # lacework_fim_runAt: "23:50"
        # lacework_fim_mode: "enable"
        # lacework_fim_noatime: "true"
        # lacework_interfaceConnectionSize: "512B"
        # lacework_memLimit: "750M"
        # lacework_perfMode: "lite"
        # lacework_proxyUrl: "http://Your_Proxy_Server:Your_Port"
        # lacework_serverurl: "Your_API_Endpoint"

        # lacework_tags:
        #   foo: "bar"
        #   test: "var"
        #   classic: "false"

      roles:
        - mrjoshuap.lacework_agent_ansible_role

## License

MIT
