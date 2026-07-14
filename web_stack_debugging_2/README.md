# Web Stack Debugging #2

## Description
This project focuses on running commands and services as non-root users —
an important security practice on Linux systems.

## Task 0: Run software as another user
File: `0-iamsomeoneelse`

Writes a Bash script that accepts a username as an argument and runs the
`whoami` command as that user, without permanently switching the current
session.

### Notes
Some system users (like `www-data`) have a login shell set to something like
`nologin`, which blocks `su` from running commands as them by default. This
is solved by explicitly specifying a working shell with `su -s /bin/sh`.

### Verified
```bash
./0-iamsomeoneelse www-data
www-data
whoami
root
```

## Author
Alier Akuang Alier Piel — Software Engineering student, African Leadership
University (ALU)
