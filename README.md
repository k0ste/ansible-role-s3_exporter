# ansible-s3_exporter

Role for deploy Prometheus
[s3_exporter](https://github.com/ribbybibby/s3_exporter)

Prefer to use fork with better functions
[s3_exporter](https://github.com/qaoru/s3_exporter)

## Requirements

* Ansible 3.0.0+;

Example configuration
-------------------------

```yaml
s3_exporter:
  # Install/upgrade exporter package, otherwise binary from Github will
  # be installed
  - install_package: 'true'
  # 'present' (do nothing if package is already installed) or 'latest' (always
  # upgrade to last version)
    package_state: 'latest'
  # version of the exporter in case of Github deployment (not relevant for
  # package deployment): bare value, like '0.8.0' or latest' - the latest
  # release from Github
    version: 'latest'
    # enable exporter service or not
    enable: 'true'
    # restart exporter service or not
    restart: 'true'
    # The configuration of s3_exporter
    settings:
      # S3 Access Key
      - aws_access_key: 'access_key'
      # S3 Secret Key
        aws_secret_key: 'secret_key'
      # Se Region
        aws_region: 'us-east-1'
      # Address to listen on for web interface and telemetry
        web_listen_address: ':9340'
      # Path under which to expose metrics
        web_metrics_path: '/metrics'
      # Path under which to expose the probe endpoint
        web_probe_path: '/probe'
      # Path under which to expose service discovery
        web_discovery_path: '/discovery'
      # S3 Endpoint
        s3_endpoint_url: 'objects.dreamhost.com'
      # Disable SSL for S3 endpoint or not
        s3_disable_ssl: 'fasle'
      # Force path style for S3
        s3_force_path_style: 'true'
      # Disable TLS certificate verification
        http_tls_insecure: 'false'
      # HTTP Timeout
        http_timeout: '10'
    # Only log messages with the given severity or above. Valid levels:
    # 'debug', 'info', 'warn', 'error', 'fatal'
        log_level: 'info'
    # Set the log target and format
    # Example: 'logger:syslog?appname=bob&local=7' or 'logger:stdout?json=true'
        log_format: 'logger:stdout'
```
