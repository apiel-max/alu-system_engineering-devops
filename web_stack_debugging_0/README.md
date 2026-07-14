# Web Stack Debugging #0

## Description
This project practices debugging a broken web stack running inside a Docker
container. The container `holbertonschool/265-0` was supposed to serve a
page containing "Hello Holberton" on port 80, but the page failed to load.

## Task 0: Give me a page!
File: `0-give_me_a_page`

### Diagnosis
- Started the container: `docker run -p 8080:80 -d -it holbertonschool/265-0`
- Confirmed the bug: `curl 0:8080` returned a connection error
- Connected to the container: `docker exec -ti <container_id> /bin/bash`
- Checked if Apache was installed: `which apache2` → confirmed installed
- Checked if Apache was running: `service apache2 status` → not running
- Started Apache: `service apache2 start`
- Verified the fix: `curl 0:8080` → returned "Hello Holberton"

### Fix
The Apache web server was installed but never started inside the container.
Starting it with `service apache2 start` resolved the issue.

## Author
Alier Akuang Alier Piel — Software Engineering student, African Leadership
University (ALU)
