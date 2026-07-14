# Web Stack Debugging #3

## Description
Debugging a WordPress site running on a LAMP stack, returning an Apache
500 Internal Server Error, using strace to trace the root cause at the
system call level. The fix is automated using Puppet instead of Bash.

## Task 0: Strace is your friend
File: `0-strace_is_your_friend.pp`

### Diagnosis
Used `strace` attached to the running Apache process, combined with `curl`
to trigger the error, to trace the exact system call failure causing the
500 error.

### Fix
Applied via a Puppet `exec` resource that corrects the underlying issue
found through strace.

## Author
Alier Akuang Alier Piel — Software Engineering student, African Leadership
University (ALU)
