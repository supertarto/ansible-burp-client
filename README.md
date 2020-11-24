# Ansible Burp-Client


[![CI](https://github.com/supertarto/ansible-burp-client/workflows/CI/badge.svg?event=push)](https://github.com/supertarto/ansible-burp-client/actions?query=workflow%3ACI)

Install and configure a burp client with ansible. This role is meant to suits my need and is inspired by https://github.com/CoffeeITWorks/ansible_burp2_client
If you want a more complete role, go check it!

## Tested plateform
* Debian 10 (Buster)

## Role variables

```yml
burpcli_force_reinstall: false
The path where the burp sources will be download and the format of the archive.
```yml
burpcli_download_dir: "{{ ansible_env.HOME }}/burp"
burpcli_srcext: 'zip'
```
Burp Version.
```yml
burpcli_version: "2.2.18"
```
The .configure command line and some path used by Burp.
```yml
burpcli_src: "burp-{{ burpcli_version }}"
burpcli_url: "https://github.com/grke/burp/archive/{{ burpcli_version }}.{{ burpcli_srcext }}"
# Doc CFLAGS here: https://github.com/grke/burp/wiki/Performance-Tips#optional-compile-time-improvements
burpcli_configure_line: "./configure"
burpcli_logs: "/var/log/burp"
burpcli_ca_csr_dir: "{{ burpcli_etc_path }}/burp/CA-client"
burpcli_etc_path: '/etc'
burpcli_usr_path: '/usr/local'
burpcli_bin_path: "{{ burpcli_usr_path }}/sbin/burp"
```
Variables used in the burp.conf file. You must adapt those to suits your infrastructure needs.
```yml
burpcli_client_progress_counter: "1"
burpcli_client_server: "192.168.1.2"

burpcli_client_cname: client1
burpcli_client_port: "4971"
burpcli_client_status_port: "4972"

burpcli_client_encryption_password: "ChangeIT!"

burpcli_client_pidfile: "/var/run/burp.pid"
burpcli_client_password: "password"
burpcli_client_protocol: "1"
burpcli_client_syslog: "0"
burpcli_client_ca_burp_ca: "{{ burpcli_usr_path }}/sbin/burp_ca"
burpcli_client_ca_csr_dir: "{{ burpcli_etc_path }}/burp/CA-client"
burpcli_client_ssl_cert_ca: "{{ burpcli_etc_path }}/burp/ssl_cert_ca.pem"
burpcli_client_ssl_cert: "{{ burpcli_etc_path }}/burp/ssl_cert-client.pem"
burpcli_client_ssl_key: "{{ burpcli_etc_path }}/burp/ssl_cert-client.key"
burpcli_client_ssl_key_password: "password"
burpcli_client_ssl_peer_cn: "burpserver"

burpcli_client_server_can_override_includes: "1"
```
List of folders/files to include/exclude. Used in burp.conf. Can be configured in the server.
```yml
burpcli_client_includes: []
burpcli_client_excludes: []
```

## Installation
```
ansible-galaxy install supertarto.burp_client
```
## License
GPL V3.0
