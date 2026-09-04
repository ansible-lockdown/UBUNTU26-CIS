# Initial Ubuntu26 CIS V1.0.0 August 2026

## September 2026 - QA pass fixes

- latest branch
  - 2.2.1, 2.3.2.2, 2.3.3.3: added the missing patch tag, --tags patch skipped them
  - 5.4.1.2, 6.1.1.1.1/4/5, 6.1.2.4/5/7 and the journald conf.d helper: added patch beside audit
  - 5.1.5: goss vars now emit nothing when the sshd access list is empty
  - 5.3.2.1: pam_unix.j2 renamed to unix.j2 to match the src the task resolves
  - auditd exception template: prefixed allow_auditd_uid_user_exclusions
  - remount_tmp: /tmp mount-busy tasks flattened, each carries listen
  - unix.j2: kept the newline after the Password stanza, it was joining Password-Initial

## September 2026 - audit variables moved to defaults

- latest branch
  - defaults split into defaults/main/main.yml and defaults/main/audit.yml
  - vars/audit.yml moved to defaults/main/audit.yml, audit toggles moved in with it
  - audit settings now overridable from inventory, group_vars, host_vars and molecule
  - prelim include_vars of audit.yml removed, defaults/main/ auto-loads
  - molecule sets audit_content and audit_conf_source in converge vars

## September 2026 - contributing guidelines

- CONTRIBUTING.md replaced with the canonical org-wide copy. It now states that pull
  requests come from approved contributors, how to be onboarded through the Discord
  server, and that issues remain open to everyone
- README gained a Contributing section under Community pointing at CONTRIBUTING.md
- Emoji removed from README headings

## September 2026 - three-way alignment to v1.0.0

Remediation task titles, audit goss titles and the v1.0.0 benchmark JSON now agree on
all 350 controls.

- 2.2.1 "Ensure NIS Client is not installed" -> "Ensure nis client is not installed"
- 5.4.2.5 "Ensure root PATH Integrity" -> "Ensure root path integrity"
- 6.2.3.32 and 6.2.3.33 restored the benchmark's quoting around the syscall names
  ("init_module", "finit_module", "delete_module"); the task names are single-quoted
  YAML scalars so the inner double quotes are literal
- separator spacing normalised to " | " in 4 task names (5.1.5, 5.1.6, 5.4.1.5,
  6.2.4.1/2/3/4) - a missing space made the title parsers read the suffix as part of
  the control title

## September 2026 - silent no-op fixes

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

