# SSH Server Hardening

## Objective
Secure the OpenSSH server by restricting root access,
limiting authentication attempts, and disabling
unnecessary forwarding features.

## Configuration Changes

- PermitRootLogin: no
- MaxAuthTries: 3
- PermitEmptyPasswords: no
- X11Forwarding: no
- LoginGraceTime: 60
- AllowUsers: joshlab

## Configuration Files

- /etc/ssh/sshd_config
- /etc/ssh/sshd_config.d/

## Verification

Validated configuration using:

sudo sshd -t

Checked effective settings using:

sudo sshd -T

Reloaded SSH service using:

sudo systemctl reload sshd

## Result

SSH configuration passed syntax validation.
Effective SSH settings confirmed the intended
security restrictions.

## Security Benefits

- Prevents direct root SSH login.
- Limits authentication attempts.
- Restricts SSH access to an approved user.
- Disables X11 forwarding.
- Prevents empty-password authentication.
