# Load Balancer Project

## Description
This project builds on the previous Web Server project by introducing a
second web server (web-02) and a load balancer (lb-01) to distribute traffic
between web-01 and web-02. The goal is to add redundancy to the web stack —
if one server fails, the other can still handle requests — and to practice
configuring HAProxy for round-robin load balancing.

## Servers
| Name        | Username | IP             |
|-------------|----------|----------------|
| 7096-web-01 | ubuntu   | 52.87.152.142  |
| 7096-web-02 | ubuntu   | 18.212.11.96   |
| 7096-lb-01  | ubuntu   | 34.239.104.222 |

## Tasks

### 0. Double the number of webservers
File: `0-custom_http_response_header`

Configures Nginx on both web-01 and web-02 to include a custom HTTP response
header, `X-Served-By`, whose value is the hostname of the server that handled
the request. This allows tracking which server answered a given request once
traffic is distributed by the load balancer.

Verified with:
```bash
curl -sI 52.87.152.142 | grep X-Served-By   # X-Served-By: 7096-web-01
curl -sI 18.212.11.96  | grep X-Served-By   # X-Served-By: 7096-web-02
```

### 1. Install your load balancer
File: `1-install_load_balancer`

Installs and configures HAProxy on lb-01 to distribute incoming HTTP requests
between web-01 and web-02 using the roundrobin algorithm. HAProxy is managed
via an init script (not systemctl), per project requirements.

## Requirements
- All scripts start with `#!/usr/bin/env bash`
- Second line of each script is a comment explaining its purpose
- All scripts pass Shellcheck without errors
- All scripts are executable and configure a brand-new Ubuntu machine with
  no manual intervention
- `systemctl` is not used anywhere in these scripts

## Author
Alier Akuang Alier Piel — Software Engineering student, African Leadership
University (ALU)
