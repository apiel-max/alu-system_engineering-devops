# Web Stack Debugging #4

## Description
Load-testing an Nginx web server with ApacheBench (ab) revealed a high
failure rate under concurrent traffic. This project diagnoses and fixes
the underlying Nginx configuration issue, automated with Puppet.

## Task 0: Sky is the limit, let's bring that limit higher
File: `0-the_sky_is_the_limit_not.pp`

### Diagnosis
Ran `ab -c 100 -n 2000 localhost/` to simulate 2000 requests at 100
concurrent connections. A large number of requests failed. Checked
`/var/log/nginx/error.log` and the `worker_connections` directive in
`/etc/nginx/nginx.conf`, which was set too low to handle the concurrent
load, causing Nginx to reject or drop excess connections.

### Fix
Applied via a Puppet `exec` resource that increases `worker_connections`
to a higher value (1024) and reloads Nginx to apply the change.

### Verified
Re-running `ab -c 100 -n 2000 localhost/` after the fix showed:
