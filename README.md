# Ansible DC/OS modules

This can be used to control DC/OS.

Requirements: Python 3 and 'dcoscli' package installed, e.g.
`pip install dcoscli`

Note: this has only been tested with DC/OS 1.10 and 'dcoscli' package version 0.5.x

Examples:

    ---
    - name: Connect to cluster
      dcos_connection:
        url: https://dcos-cluster.example.com
        username: sysadmin
        password: "{{ sysadm_pwd }}"

    - name: Ensure Spark is installed
      dcos_package:
        name: spark
        state: present
        version: 2.0.1-2.2.0-1


These commands use the `dcos` and `dcoscli` pip packages. However, it is also possible
to use the commands suffixed with `_cli` which use the CLI directly. This is probably
more compatible across different versions as the pip packages may not have a stable API.

Examples:

    ---
    - name: Connect to cluster
      dcos_connection_cli:
        url: https://dcos-cluster.example.com
        username: sysadmin
        password_file: /path/to/file.txt

    - name: Ensure Jenkins is not installed
      dcos_package_cli:
        name: jenkins
	app_id: jenkins
        state: absent

For more documentation about the modules please check the documentation in the modules
subdirectory.
