# Initial Ubuntu26 CIS V1.0.0 August 2026

## CIS Benchmark 1.0.0

## November 2026 - 1.0.0 public

- workflow updates
- pre-commit update

## October 2026 - QA fixes

- audit binary switched from goss to syver v0.15.1
- prelim_goss_available renamed prelim_audit_bin_available
- README audit section describes syver
- 7.2.9 and 7.2.10 home directory discovery runs when either control is enabled
- 7.2.7 and 7.2.8 duplicate name warnings use the registered variable
- task level tags aligned to Profile Applicability, 33 tasks
- 1.1.2.1.1 to 1.1.2.7.1 missing partition warnings now fire
- 1.1.2.3.1 /home warning checks the /home mount
- 5.2.5 sudoers discovery gated on 5.2.5 only, rule_5.2.6 tag removed
- 5.3.2.1 to 5.3.2.4 pam discovery tasks run in check mode
- 5.3.3.2.1 to 5.3.3.2.7 pwquality config discovery gated and tagged
- 6.2.4.5 to 6.2.4.7 audit file discovery tagged
- 6.2.4.1 sets the mode on each audit log file, not the log directory
- 6.2.4.4 keeps owner access on the audit log directory
- 1.3.1.3 and 1.3.1.4 apparmor profile glob now expands, failures reported
- 5.3.3.1.1 to 5.3.3.1.3 faillock regexps fixed
- 5.4.1.6 current date computed in a shell
- 7.2.2 empty password accounts looped individually
- 5.4.2.2 GID 0 members looped individually
- 7.2.8 checks group names
- 3.2.3 blacklists dccp
- 2.1.6 vsftpd package name corrected
- 2.1.16 masks inetutils-inetd.service
- 5.2.6 timestamp_timeout regexp fixed
- 5.2.2 sudoers edit validated with visudo
- 6.1.2.6 imtcp regexps escape the parentheses
- 2.1.3 removes or masks the kea DHCP server packages and units
- 3.1.2 wireless discovery runs in a shell so the glob expands
- 5.3.3.4.4 adds use_authtok when pam_unix lacks it
- 6.1.3.1 lastlog, wtmp and btmp get their own mode
- 1.2.1.3 sets owner and mode on non-conforming gpg key files
- 1.6.10 uses ubtu26cis_sshd_banner_file
- 2.2.1 nis client gated on ubtu26cis_nis_client_required
- 2.2.4 and 2.2.6 remove every listed client package
- 5.2.1 installs sudo-rs by default
- 5.4.3.1 removes nologin lines from /etc/shells
- 6.1.1.1.4 checks the /etc/tmpfiles.d override, vendor file left alone
- 6.1.1.1.5 journald rotation defaults set to the benchmark example values
- 1.5.11 and 1.5.12 coredump settings written to a coredump.conf.d drop-in under [Coredump]
- 1.2.1.6 and 1.2.1.9 set owner and mode per file and report changes
- 2.1.22 exim4 changes run update-exim4.conf
- 2.3.3.3 unmasks chrony before starting it
- 2.4.2.1 runs only when at is installed, group daemon when present
- 3.2.1 to 3.2.6 unload the module
- 5.4.3.2 sets TMOUT with typeset -xr
- 6.1.2.4 finds the rsyslog config in /etc/rsyslog.conf and rsyslog.d only
- 7.1.11 sticky bit step skips when no directories are found
- route flush handlers use sysctl -w and no longer write /etc/sysctl.conf
- auditd user exclusions exclude the listed users, not everyone else
- ubtu26_ptrace_value renamed ubtu26cis_ptrace_value
- tasks that change files named PATCH in 1.1.1.11, 5.4.2.5, 5.4.3.2 and 7.2.10
- bridge passes ubtu26cis_tmp_svc to the audit
- 6.1.2.2 unmasks and starts rsyslog
- 6.1.2.4 auth logging goes to /var/log/auth.log
- 6.2.3.18 and 6.2.3.25 rules include fchmodat2 and renameat2
- 6.2.3.32 and 6.2.3.33 rules cover b32 and use auid!=unset
- 6.2.3.x watch rules use -a always,exit -F path= and -F dir= instead of the deprecated -w
- 6.2.3.4 clock_settime rule filters a0=0x0, localtime rule keyed localtime-change
- 6.2.3.8 watches /etc/network/interfaces, interfaces.d and /etc/netplan
- 6.2.3.27 to 6.2.3.31 rules set arch=b64 and auid!=unset
- 6.2.3.34 -c written to 01-initialize.rules
- auditd rule files written 0640 so 6.2.4.5 does not change them on the next run
- 6.2.3.8 and 6.2.3.9 directory rules written only when the directory exists
- 6.3.2 cron service task no longer reports changed every run
- 6.3.2 defaults to dailyaidecheck.timer, the benchmark method
- README example audit summary, links and defaults comments corrected
- 6.3.2 timer path keeps the packaged dailyaidecheck.service and no longer starts a scan each run
- 6.3.3 and audit_bins no longer list autrace
- 7.1.11 world-writable file fix no longer updates file timestamps
- AIDE timer OnCalendar order fixed
- warn_control_id set on the warning task, not the block
- WARN and WARNING task kinds renamed AUDIT
- duplicate system_is_container default removed
- unused ubtu26cis_ipv4_required and legacy_boot bridge entry removed
- molecule scenarios run the role via roles:, read-only role_name var removed
- 1.1.1.11, 3.2.7 and 6.2.3.36 named AUDIT, scored tag removed
- ufw IPT_SYSCTL and log_martians tasks no longer tagged always
- ufw outbound allow tasks tagged rule_4.1.4
- pam-configs templates no longer start with the managed-by header
- /tmp systemd handler enables and unmasks tmp.mount
- /tmp mount busy warning now fires
- auditd handlers tolerate a skipped immutable check or augenrules check
- duplicate Grub update handler removed
- unused iptables handlers removed
- octal and absolute file modes made relative
- register placed after changed_when and failed_when
- 3.1.2 wireless discovery register renamed to discovered_wireless_adapters
- ansible_env and ansible_local replaced with ansible_facts
- meta platform version set to resolute
- Company name updated to MindPoint Group - A Quantum Sky Company
- unused ubtu26cis_skip_for_test removed
- bridge template rule section end marker added
- bridge passes ubtu26cis_dconf_db_name through to the audit
- bridge passes ubtu26cis_warning_banner through to the audit
- 5.1.13 and 5.1.14 KexAlgorithms include mlkem768x25519-sha256 and sntrup761x25519-sha512
- 5.1.5 to 5.1.24 sshd settings written to /etc/ssh/sshd_config.d/00-cis-sshd.conf so other drop-ins cannot override them
- sshd_config keeps its Include line, CIS keywords placed above it are commented out
- bridge passes ubtu26cis_sshd_cis_conf to the audit
- 6.2.3.21 toggle moved into numeric order
- remove schedules from workflows

## September 2026

- 2.2.1, 2.3.2.2, 2.3.3.3: added the missing patch tag, --tags patch skipped them
- 5.4.1.2, 6.1.1.1.1/4/5, 6.1.2.4/5/7 and the journald conf.d helper: added patch beside audit
- 5.1.5: goss vars now emit nothing when the sshd access list is empty
- 5.3.2.1: pam_unix.j2 renamed to unix.j2 to match the src the task resolves
- auditd exception template: prefixed allow_auditd_uid_user_exclusions
- remount_tmp: /tmp mount-busy tasks flattened, each carries listen
- unix.j2: kept the newline after the Password stanza, it was joining Password-Initial
- defaults split into defaults/main/main.yml and defaults/main/audit.yml
- vars/audit.yml moved to defaults/main/audit.yml, audit toggles moved in with it
- audit settings now overridable from inventory, group_vars, host_vars and molecule
- prelim include_vars of audit.yml removed, defaults/main/ auto-loads
- molecule sets audit_content and audit_conf_source in converge vars
- CONTRIBUTING.md replaced with the canonical org-wide copy. It now states that pull
  requests come from approved contributors, how to be onboarded through the Discord
  server, and that issues remain open to everyone
- README gained a Contributing section under Community pointing at CONTRIBUTING.md
- Emoji removed from README headings
- 2.2.1 "Ensure NIS Client is not installed" -> "Ensure nis client is not installed"
- 5.4.2.5 "Ensure root PATH Integrity" -> "Ensure root path integrity"
- 6.2.3.32 and 6.2.3.33 restored the benchmark's quoting around the syscall names
  ("init_module", "finit_module", "delete_module"); the task names are single-quoted
  YAML scalars so the inner double quotes are literal
- separator spacing normalised to " | " in 4 task names (5.1.5, 5.1.6, 5.4.1.5,
  6.2.4.1/2/3/4) - a missing space made the title parsers read the suffix as part of
  the control title
- 6.2.3.x auditd: the privileged command exclude rendered `(asdfmnop|)` when
  `ubtu26cis_priv_command_excluded_mounts` is empty (the default), an empty alternative
  that GNU grep matches against every line, so `grep -Ev` discarded every mount and no
  privileged commands were found. The alternation is now gated on a non-empty list
- 6.2.3.x auditd: the task registered `discovered_privileged_commands` but
  `templates/audit/99_auditd.rules.j2` reads `discovered_privilege_processes` behind an
  `is defined` guard, so no `-k privileged` rules were ever written. Register renamed
- 7.1.13 used `find ... -perm \( -02000 or -04000 \)`; find takes `\(` as the mode
  argument and `or` is not a find operator, so with `failed_when: false` the SUID/SGID
  review reported clean on every host. Now `\( -perm -02000 -o -perm -04000 \)`
- 3.2.1-3.2.6 modprobe tasks looped two lines against one fixed regexp, so the second
  item replaced what the first wrote and only the blacklist line survived. Each item now
  carries its own regexp, and the regexps moved to double quotes - in a single-quoted
  YAML scalar `\\s` stays literal and can never match
- 3.1.2 wrote `install <mod> true` with a regexp naming "true" rather than the module;
  now `/bin/true` and the module name

## Alignment to CIS Ubuntu Linux 26.04 LTS Benchmark v1.0.0 - August 2026

Full control alignment against v1.0.0 (350 controls). All rule IDs, task names and
toggles now match the benchmark exactly.

