# Work Breakdown Structure (WBS)

Below is the hierarchical WBS for the project:

## 1. Project Initiation
- **1.1** Define project goals and scope.
- **1.2** Identify resources and timelines.

## 2. SSH Hardening
- **2.1** Disable root login and empty passwords.
- **2.2** Restrict SSH to Port 22 and Protocol 2.
- **2.3** Restart SSH service and validate changes.

## 3. User and Group Management
- **3.1** Remove terminated staff accounts and home directories.
- **3.2** Lock accounts for staff on temporary leave.
- **3.3** Unlock accounts for active employees.
- **3.4** Move marketing group users to the research group.
- **3.5** Delete the marketing group.

## 4. Password Policy Enforcement
- **4.1** Update `/etc/pam.d/common-password`.
- **4.2** Test password policy enforcement.

## 5. Logging Configuration
- **5.1** Enable persistent logging in `journald.conf`.
- **5.2** Configure log rotation in `logrotate.conf`.

## 6. Service Management
- **6.1** Identify running unnecessary services (e.g., MySQL, Samba).
- **6.2** Stop, disable, and remove unnecessary services.
- **6.3** Verify removal.

## 7. File and Script Permissions
- **7.1** Remove world permissions in `/home`.
- **7.2** Restrict script access for:
  - **Engineering scripts**
  - **Research scripts**
  - **Finance scripts**

## 8. Automation and Scheduling
- **8.1** Develop `hardening_script1.sh`.
- **8.2** Develop `hardening_script2.sh`.
- **8.3** Schedule scripts using cron jobs:
  - **Monthly** for `hardening_script1.sh`.
  - **Weekly** for `hardening_script2.sh`.

## 9. Testing and Final Reporting
- **9.1** Test all configurations and changes.
- **9.2** Summarize findings and remaining concerns.
- **9.3** Deliver final report.
