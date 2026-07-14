# Web Stack Debugging #1

## Description
Debugging why Nginx, though installed, was not listening on port 80 inside
an Ubuntu 20.04 Docker container.

## Task 0: Nginx likes port 80
File: `0-nginx_likes_port_80`

### Diagnosis
- Installed Nginx: `apt install -y nginx`
- Checked status: `service nginx status` → not running
- Investigated why: found `/usr/sbin/policy-rc.d` containing `exit 101`,
  which blocks services from auto-starting inside minimal Docker base images
- Manually started Nginx: `service nginx start` → succeeded
- Verified with `curl` from the host machine, mapped to the container's
  port 80, returned the default Nginx welcome page

### Fix
Nginx was correctly installed but never started, due to policy-rc.d blocking
automatic service startup in this container image. Starting it manually with
`service nginx start` resolves the issue.

## Author
Alier Akuang Alier Piel — Software Engineering student, African Leadership
University (ALU)
