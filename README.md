# ansible-s3_exporter

Role for deploy Prometheus
[s3_exporter](https://github.com/ribbybibby/s3_exporter)

## Requirements

* Ansible 3.0.0+;

Example configuration
-------------------------

```yaml
s3_exporter:
  # version of the exporter:
  # bare value, like '1.5.2'
  # 'latest' - the latest release from Github
  - version: 'latest'
    # enable exporter service or not
    enable: 'true'
    # restart exporter service or not
    restart: 'true'
    # The configuration of s3_exporter
    settings:
      - access_key: 'secret'
        secret_key: 'secret'
        region: 'us-east-1'
        web_listen_address: ':9340'
        web_metrics_path: '/metrics'
        web_probe_path: '/probe'
        web_discovery_path: '/discovery'
        endpoint_url: 'objects.dreamhost.com'
        disable_ssl: 'fasle'
        force_path_style: 'true'
    # Only log messages with the given severity or above. Valid levels:
    # 'debug', 'info', 'warn', 'error', 'fatal'
        log_level: 'info'
    # Set the log target and format
    # Example: 'logger:syslog?appname=bob&local=7' or 'logger:stdout?json=true'
        log_format: 'logger:stdout'
```
