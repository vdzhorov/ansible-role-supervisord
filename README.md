# Ansible Role: Supervisord

Installs Supervisor on Ubuntu 24.04 and manages programs via `conf.d` drop-ins. Manages Supervisor programs if needed.

## Requirements

None

## Role Variables

See `defaults/main.yml` for all options. Key var is `supervisor_programs`, see an example bellow:

```yaml
supervisor_programs:
  - name: my_nodejs_app
    command: /usr/bin/node /home/myapp/index.js
    directory: /home/myapp
    user: myapp
    autostart: true
    autorestart: true
    stdout_logfile: /home/myapp/logs/myapp_logs.log
    stderr_logfile: /home/myapp/logs/myapp_logs_err.log
    stopsignal: TERM
    environment:
      NODE_ENV: production
      PORT: "3000"
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - geerlingguy.docker
```

## Dependencies

None

## License

MIT

## Author Information

This role was created by Valentin Dzhorov in 2025 due to necessity. There were no clean Supervisord roles at the moment of the role creation, which installed and condigured (optionally) Supervisord programs.
