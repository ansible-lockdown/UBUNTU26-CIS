# Initial Ubuntu26 CIS V1.0.0 August 2026

## Alignment to CIS Ubuntu Linux 26.04 LTS Benchmark v1.0.0 - August 2026

Full control alignment against v1.0.0 (350 controls). All rule IDs, task names and
toggles now match the benchmark exactly.

### Section 1

- Added missing 1.1.1.9 (firewire-core kernel module); renumbered usb-storage to
  1.1.1.10 and unused filesystem modules to 1.1.1.11
- Rewrote 1.2.1.x as the 15 v1.0.0 APT repository controls (Signed-By, weak
  dependencies, gpg key/keyring/sources.list.d access, https repositories,
  AllowInsecureRepositories, AllowWeakRepositories,
  AllowDowngradeToInsecureRepositories, Acquire::Check-Date)
- AppArmor: 1.3.1.3 is now "all AppArmor Profiles are enforcing"; added new
  1.3.1.4 kernel.apparmor_restrict_unprivileged_unconfined sysctl control.
  Removed the control_1_3_1_4_was_run cross-block fact
- Added 1.5.6 - 1.5.12 (prelink, automatic error reporting, kernel.kptr_restrict,
  kernel.randomize_va_space, core file size, systemd-coredump ProcessSizeMax and
  Storage)
- Section 1.6 corrected: added missing 1.6.4 (pam_motd is configured) and 1.6.5
  (sshd warning Banner is configured); removed duplicate access controls that
  shadowed 1.6.7/1.6.8; added 1.6.9 - 1.6.12 (pam_motd and sshd banner access,
  update-notifier-motd service and timer)
- GDM 1.7.x reduced from 10 to the 7 v1.0.0 controls; lock-override tasks merged
  into their parent control; added 1.7.7 Xwayland

### Section 2

- Added 2.1.16 (telnet server services) - subsequent 2.1.x controls renumbered
- Added 2.4.1.7 (access to /etc/cron.yearly)

### Section 3

- 3.2.x reordered to benchmark order and extended to 7 controls (atm, can, dccp,
  rds, sctp, tipc, unneeded network protocols)
- 3.3.x split from a flat 11 controls into 3.3.1.1 - 3.3.1.19 (IPv4) and
  3.3.2.1 - 3.3.2.8 (IPv6), one control per sysctl parameter

### Section 4

- Section 4 now covers UFW only, matching the benchmark's 5 controls
  (4.1.1 - 4.1.5). The nftables and iptables alternative firewall profiles and
  the ubtu26cis_firewall_package toggle have been removed

### Section 5

- Added 5.1.2 (access to /etc/ssh/sshd_config.d directory), 5.1.14 (post-quantum
  key exchange algorithms), 5.1.21 (PermitEmptyPasswords) and 5.1.22
  (PermitRootLogin); 5.1.x renumbered to match
- Added 5.3.1.4 (cracklib-runtime)

### Section 6

- Journald consolidated under 6.1.1.1.1 - 6.1.1.1.7
- Rsyslog renumbered to 6.1.2.1 - 6.1.2.10, adding rsyslog-gnutls, gtls
  forwarding and CA certificate controls
- Logfile access moved to 6.1.3.1
- Auditd rules extended from 21 to 36 controls (6.2.3.1 - 6.2.3.36), including
  sethostname/setdomainname, /etc/issue, /etc/hosts, /etc/NetworkManager,
  shadow/gshadow, opasswd, nsswitch.conf, pam.conf, split DAC permission
  modification syscalls, unlink/rename deletion, init_module/finit_module,
  delete_module and audit configuration load-on-error

### Section 7

- Added 7.2.11 (local interactive user dot directories access)

### Fixes

- journald storage.conf.j2 gated Compress and Storage on rsyslog rule variables
  instead of the journald ones, so the journald toggles had no effect
- vars/is_container.yml referenced AppArmor rules under the old flat numbering
  and a non-existent 6.2.4.11, and did not cover auditd rules 6.2.3.22 - 6.2.3.36
- Task titles aligned to the benchmark wording across all 350 controls
