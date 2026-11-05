# RHEL Enterprise Linux Server Hardening

## Project Overview

This project documents the assessment, security hardening, configuration and verification of a Red Hat Enterprise Linux (RHEL) 10.2 server running in Oracle VirtualBox.

The objective is to apply practical enterprise Linux security administration techniques to improve system security, strengthen authentication and access controls, and reduce unnecessary exposure.

## Environment

- Operating System: Red Hat Enterprise Linux 10.2
- Kernel: Linux 6.12
- Architecture: x86_64
- Virtualization: Oracle VirtualBox
- Shell: Bash
- Administrative tools: DNF, systemd, firewalld, SELinux, OpenSSH

## Project Objectives

- Perform an initial security assessment.
- Implement strong password policies.
- Configure account lockout protection.
- Harden SSH remote access.
- Verify security configurations.
- Document implementation and audit results.

## Implemented Security Controls

### 1. Password Policy

Configured password quality enforcement using PAM and libpwquality.

Implemented:
- Minimum password length of 12 characters.
- Minimum of 4 character classes.
- Maximum of 3 consecutive repeated characters.
- Maximum of 3 consecutive sequential characters.
- User password similarity checking.
- Password quality enforcement for root.

Configuration:
`/etc/security/pwquality.conf`

### 2. Account Lockout Policy

Implemented failed authentication protection using faillock.

Configuration:
`/etc/security/faillock.conf`

Security settings:
- Maximum failed attempts: 5.
- Failure interval: 900 seconds.
- Account unlock duration: 600 seconds.
- Root account lockout enforcement enabled.

Enabled the faillock feature through authselect.

### 3. SSH Server Hardening

Hardened OpenSSH server configuration to restrict remote access.

Configuration:
`/etc/ssh/sshd_config`

Implemented:
- Disabled direct root login.
- Limited authentication attempts to 3.
- Disabled empty passwords.
- Disabled X11 forwarding.
- Set login grace time to 60 seconds.
- Restricted SSH access to the authorized user.

Validated the configuration using `sshd -t` and `sshd -T`.

## Verification

Security configurations were checked using Linux administrative commands, including:

- `systemctl status sshd`
- `sshd -t`
- `sshd -T`
- `authselect current`
- `authselect check`
- `faillock --user USERNAME`
- `grep` for configuration verification.

## Project Structure

- `assessment/` - Initial system security assessment.
- `hardening/` - Security implementation documentation.
- `auditing/` - Verification and audit results.
- `reports/` - Project findings and reports.
- `screenshots/` - Implementation evidence.
- `scripts/` - Administrative automation scripts.

## Learning Outcomes

This project demonstrates practical experience in:

- Enterprise Linux administration.
- Linux authentication and authorization.
- PAM configuration.
- Password security enforcement.
- SSH security administration.
- Account lockout management.
- Linux security auditing.
- System configuration verification.
