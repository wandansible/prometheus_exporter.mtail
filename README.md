Ansible role: Prometheus Exporter - mtail
=========================================

Install and configure mtail for Prometheus.

Role Variables
--------------

```
ENTRY POINT: main - Install and configure mtail for Prometheus

OPTIONS (= is mandatory):

- mtail_exporter_add_extract_dir
        If true, add an extraction directory for the exporter package
        [Default: True]
        type: bool

- mtail_exporter_arch_map
        Mapping of the possible values of ansible_architecture to the
        exporter package architectures
        [Default: (null)]
        type: dict

- mtail_exporter_bin_dir
        Directory for the exporter executable
        [Default: (null)]
        type: str

- mtail_exporter_binary
        Filename for the exporter executable
        [Default: (null)]
        type: str

- mtail_exporter_checksum
        The exporter package checksum
        [Default: (null)]
        type: str

- mtail_exporter_checksum_type
        The exporter package checksum type
        [Default: (null)]
        type: str

- mtail_exporter_checksums_file
        Filename for the exporter package checksums
        [Default: (null)]
        type: str

- mtail_exporter_checksums_url
        URL for the exporter package checksums
        [Default: (null)]
        type: str

- mtail_exporter_configure_caddy
        If true, configure caddy to add a TLS endpoint for the
        exporter
        [Default: True]
        type: bool

- mtail_exporter_description
        Description for the exporter systemd service
        [Default: (null)]
        type: str

- mtail_exporter_extra_flags
        Extra flags to run exporter with
        [Default: (null)]
        type: dict

- mtail_exporter_file_sd_dir
        Directory, on scrape servers, for the file service discovery
        target
        [Default: /etc/prometheus/file_sd/mtail_exporter]
        type: str

- mtail_exporter_flags
        Contents or list of flags to run exporter with
        [Default: (null)]
        type: raw

- mtail_exporter_git_org
        Name of organisation for exporter git repository
        [Default: (null)]
        type: str

- mtail_exporter_git_repo
        Name of exporter git repository
        [Default: (null)]
        type: str

- mtail_exporter_group
        Name of the exporter unix group
        [Default: (null)]
        type: str

- mtail_exporter_groups
        Unix groups added to exporter unix user
        [Default: ['adm']]
        elements: str
        type: list

- mtail_exporter_install
        If true, install exporter
        [Default: True]
        type: bool

- mtail_exporter_labels
        Labels added to exporter metrics, overrides prometheus_labels
        [Default: (null)]
        type: dict

- mtail_exporter_latest_url
        URL for the latest version
        [Default: (null)]
        type: str

- mtail_exporter_listen
        Listen address and port
        [Default: localhost:9197]
        type: str

- mtail_exporter_log_dir
        Directory for logs
        [Default: (null)]
        type: str

- mtail_exporter_logs
        List of fileglobs for log files to be evaluated by mtail
        [Default: (null)]
        elements: str
        type: list

- mtail_exporter_manage_user
        If true, add exporter unix user and group
        [Default: True]
        type: bool

- mtail_exporter_package
        Filename of the exporter package (without extension)
        [Default: (null)]
        type: str

- mtail_exporter_package_dir
        Directory the exporter package is extracted to
        [Default: (null)]
        type: str

- mtail_exporter_package_name
        Name of the exporter package
        [Default: (null)]
        type: str

- mtail_exporter_package_url
        URL for the exporter package
        [Default: (null)]
        type: str

- mtail_exporter_port
        Listen port
        [Default: 9197]
        type: int

- mtail_exporter_programs_dir
        Directory for mtail programs
        [Default: /etc/mtail]
        type: str

- mtail_exporter_programs_files
        List of fileglobs for program files to copy to the host
        [Default: ['mtail/*.mtail']]
        elements: str
        type: list

- mtail_exporter_register
        If true, register the exporter with the scrape servers
        [Default: True]
        type: bool

- mtail_exporter_scrape_servers
        List of servers that scrape exporter metrics from the host,
        overrides prometheus_scrape_servers
        [Default: (null)]
        elements: str
        type: list

- mtail_exporter_service
        Name of the exporter systemd service
        [Default: (null)]
        type: str

- mtail_exporter_src_dir
        Directory for the exporter downloads
        [Default: (null)]
        type: str

- mtail_exporter_tag
        Version git tag
        [Default: (null)]
        type: str

- mtail_exporter_target
        Scrape target hostname and port
        [Default: (null)]
        type: str

- mtail_exporter_user
        Name of the exporter unix user
        [Default: (null)]
        type: str

- mtail_exporter_version
        Version to install (use "latest" for the latest version)
        [Default: latest]
        type: str

- mtail_exporter_version_regex
        Regular expression for capturing the version from the latest
        tag
        [Default: (null)]
        type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter,main,wandansible.prometheus_exporter
    ansible-galaxy install git+https://github.com/wandansible/prometheus_exporter.mtail,main,wandansible.prometheus_exporter.mtail
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.prometheus_exporter
      src: https://github.com/wandansible/prometheus_exporter
    - name: wandansible.prometheus_exporter.mtail
      src: https://github.com/wandansible/prometheus_exporter.mtail

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: all
      roles:
         - role: wandansible.prometheus_exporter.mtail
           become: true
