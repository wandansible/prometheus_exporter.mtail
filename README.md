Ansible role: Prometheus Exporter - mtail
=========================================

Install and configure mtail for Prometheus.

Requirements
------------

This role depends on the [base prometheus exporter role](https://github.com/wandansible/prometheus_exporter).


Role Variables
--------------

```
ENTRY POINT: *main* - Install and configure mtail for Prometheus

Options (= indicates it is required):

- mtail_exporter_arch_map  Mapping of the possible values of
                            ansible_architecture to the exporter
                            package architectures
          default: null
          type: dict

- mtail_exporter_archive_urls  Override the list of exporter archive
                                urls for different platforms and
                                architectures
          default: null
          elements: str
          type: list

- mtail_exporter_bin_dir  Directory for the exporter executable
          default: null
          type: str

- mtail_exporter_binary  Filename for the exporter executable
          default: mtail
          type: str

- mtail_exporter_checksum_type  The exporter package checksum type
          default: null
          type: str

- mtail_exporter_checksum_url  Override the URL for the exporter
                                checksum file
          default: null
          type: str

- mtail_exporter_checksums  Override exporter archive checksums file
                             contents
          default: null
          type: str

- mtail_exporter_clean_src_dir  Remove old downloaded archive files
                                 from exporter src directory
          default: true
          type: bool

- mtail_exporter_configure_caddy  If true, configure caddy to add a
                                   TLS endpoint for the exporter
          default: false
          type: bool

- mtail_exporter_description  Description for the exporter systemd
                               service
          default: null
          type: str

- mtail_exporter_extra_flags  Extra flags to run exporter with
          default: null
          type: dict

- mtail_exporter_file_sd_dir  Directory, on scrape servers, for the
                               file service discovery target
          default: /etc/prometheus/file_sd/mtail_exporter
          type: str

- mtail_exporter_flags  List of flags to run exporter with, as string
                         or list
          default: null
          type: raw

- mtail_exporter_github_checksum_filename  Filename for the exporter
                                            package checksums file on
                                            github
          default: checksums.txt
          type: str

- mtail_exporter_github_org  Name of organisation for exporter github
                              repository
          default: jaqx0r
          type: str

- mtail_exporter_github_repo  Name of exporter github repository
          default: mtail
          type: str

- mtail_exporter_github_token  Optional bearer token to use to
                                authenticate with api.github.com
          default: ''
          type: str

- mtail_exporter_group  Name of the exporter unix group
          default: null
          type: str

- mtail_exporter_groups  Unix groups added to exporter unix user
          default: [adm]
          elements: str
          type: list

- mtail_exporter_handler  Name of the exporter handler to notify
          default: null
          type: str

- mtail_exporter_install  If true, install exporter
          default: true
          type: bool

- mtail_exporter_labels  Labels added to exporter metrics, overrides
                          prometheus_labels
          default: null
          type: dict

- mtail_exporter_listen  Listen address and port
          default: localhost:9197
          type: str

- mtail_exporter_log_dir  Directory for logs
          default: null
          type: str

- mtail_exporter_logs  List of fileglobs for log files to be
                        evaluated by mtail
          default: null
          elements: str
          type: list

- mtail_exporter_manage_user  If true, add exporter unix user and
                               group
          default: true
          type: bool

- mtail_exporter_port  Listen port
          default: 9197
          type: int

- mtail_exporter_programs_dir  Directory for mtail programs
          default: /etc/prometheus/exporters/mtail
          type: str

- mtail_exporter_programs_files  List of fileglobs for program files
                                  to copy to the host
          default: [mtail/*.mtail]
          elements: str
          type: list

- mtail_exporter_register  If true, register the exporter with the
                            scrape servers
          default: false
          type: bool

- mtail_exporter_scrape_servers  List of servers that scrape exporter
                                  metrics from the host, overrides
                                  prometheus_scrape_servers
          default: null
          elements: str
          type: list

- mtail_exporter_service  Name of the exporter systemd service
          default: null
          type: str

- mtail_exporter_service_unit_file  Contents of the systemd unit file
                                     for the exporter
          default: null
          type: str

- mtail_exporter_src_dir  Directory for the downloaded exporter src
                           archive
          default: null
          type: str

- mtail_exporter_strip_components  Strip NUMBER leading components
                                    from file names on extraction
          default: 0
          type: int

- mtail_exporter_target  Scrape target hostname and port
          default: null
          type: str

- mtail_exporter_user  Name of the exporter unix user
          default: null
          type: str

- mtail_exporter_version  Version to install (use "latest" for the
                           latest version)
          default: latest
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
