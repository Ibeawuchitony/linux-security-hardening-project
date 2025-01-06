# Project Definition

## Objective
The primary objective of this project is to improve the security posture of the Linux environment by implementing hardening measures, auditing system configurations, automating key tasks, and ensuring compliance with security best practices.

##Project Goal:
To mitigate potential security vulnerabilities by removing insecure configurations, restricting privileges, enforcing strong password policies, managing user accounts, securing SSH access, improving logging practices, and automating routine system maintenance tasks.

Project Duration:
4 Weeks

## Scope
- SSH Hardening
- Logging and Auditing
- Password Policy Enforcement
- File and Directory Permissions
- Service Management
- SSH Hardening:

	- Disable root login and empty password usage.
	- Restrict SSH to Protocol 2 and Port 22.
	- User and Group Management:

- Remove accounts of terminated staff, including home directories.
	- Lock user accounts for staff on temporary leave.
	- Unlock user accounts for active employees.
	- Move employees from the marketing group to the research group.
	- Remove the deprecated marketing group.

- Password Policy Enforcement:

	- Update /etc/pam.d/common-password with:
	- Minimum password length:
		8 characters
		At least 1 uppercase letter and 1 special character
		Retry limit: 2 attempts.
	- Update password Hashing configuration

- Logging Configuration:

	- Enable persistent logging in journald.conf.
	- Configure log rotation in logrotate.conf:
		Rotate logs daily.
		Retain logs for 7 days.

- Service Management:

	- Identify and remove unnecessary services:

- File and Script Permissions:

	- Remove world permissions from sensitive files in /home.
	- Restrict script access:

- Automation of Hardening Tasks:

	- Create two scripts:
		hardening_script1.sh: For backup, permission updates, and logging.
		hardening_script2.sh: For package updates and audits.

- Schedule scripts using cron:
		hardening_script1.sh: Runs monthly on the 1st of the month.
		hardening_script2.sh: Runs weekly every Monday.


