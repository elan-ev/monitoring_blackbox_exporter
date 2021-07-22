# Ansible Role for the blackbox_exporter

![molecule](https://github.com/elan-ev/monitoring_loki/actions/workflows/molecule.yml/badge.svg)

Install the latest [blackbox_exporter](https://github.com/prometheus/blackbox_exporter) version with [ansible](https://docs.ansible.com/).

## Role Variables

Currently, there are no variable to be set, except which configuration template you want to use.
The role comes with a simple configuration, that you will likely want to extend (see the [blackbox_exporter config options](https://github.com/prometheus/blackbox_exporter/blob/master/CONFIGURATION.md) for that).
To pass your own configuration file, change the path to the template in the variable `blackbox_exporter_config_template`.

Keep in mind that you also need to configure your prometheus targets in order to scrape the results of the blackbox_exporter.

## Example Playbook

Just add the role to your playbook:

```yaml
- hosts: all
  become: true
  roles:
    - elan.monitoring_blackbox_exporter
```

## Development

For development and testing you can use [molecule](https://molecule.readthedocs.io/en/latest/).
With podman as driver you can install it like this – preferably in a virtual environment (if you use docker, substitute `podman` with `docker`):

```bash
pip install -r .dev_requirements.txt
```

Then you can *create* the test instances, apply the ansible config (*converge*) and *destroy* the test instances with these commands:

```bash
molecule create
molecule converge
molecule destroy
```

If you want to inspect a running test instance use `molecule login --host <instance_name>`, where you replace `<instance_name>` with the desired value.

## License

[BSD-3-Clause](LICENSE)

## Author Information

[ELAN e.V](https://elan-ev.de/)
