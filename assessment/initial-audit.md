# Initial Security Audit

## Findings

### Cockpit
- **Installed:** Yes
- **Socket:** Active
- **Enabled at boot:** Yes
- **Port:** 9090
- **Assessment:** Confirm whether port 9090 is reachable from untrusted networks. Restrict access to a trusted administrative network or VPN, or disable Cockpit if it is not needed.

### Automatic security updates
- **`dnf-automatic`:** Not installed
- **Automatic update timer:** Not available
- **Assessment:** Automatic security updates are not currently configured through `dnf-automatic`. Decide whether automatic installation fits the patching process; otherwise, document and follow a regular manual patch schedule.

### SSH
- **Root login:** Enabled
- **Password authentication:** Enabled
- **Public-key authentication:** Enabled
- **Assessment:** Root and password-based SSH logins are permitted. Confirm that key-based access works before restricting access, then consider disabling root SSH login and password authentication.

### Failed system services
- **Finding:** One or more system services failed; service names and details have not yet been recorded.
- **Assessment:** Identify the failed services and review their logs before deciding whether to repair, disable, or otherwise address them.

## Remediation plan
1. Check Cockpit's network exposure and restrict access if necessary.
2. Choose and document an approach for timely security updates; configure `dnf-automatic` if appropriate.
3. Verify key-based SSH access, then restrict root and password-based SSH login where operationally appropriate.
4. Identify failed services and investigate their logs and cause.

## Scope and limitations
This is an initial snapshot of the checks recorded above, not a complete security assessment. Network reachability, service failure details, and the effectiveness of SSH key-based access still need to be verified.
