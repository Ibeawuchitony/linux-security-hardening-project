##  Summary Report

Completed Tasks Checklist
	1. Hardening SSH:
		○ Disabled SSH login for root users.
		○ Disabled SSH with empty passwords.
		○ Restricted SSH to Port 2222. Port 22 is already in use by another service
		○ Enabled SSH Protocol 2.
	2. Package Management:
		○ Updated the package manager and upgraded all installed packages.
		○ Removed insecure packages (telnet and rsh-client).
		○ Installed security tools: ufw, lynis, and tripwire.
	3. Logging Configuration:
		○ Configured journald.conf:
			§ Set Storage=persistent for persistent log storage.
			§ Limited log size with SystemMaxUse=300M.
		○ Configured log rotation in /etc/logrotate.conf:
			§ Changed log rotation frequency to daily.
			§ Retained logs for 7 days.
	4. File and Directory Permissions:
		○ Removed world permissions (read, write, execute) from all files in /home.
		○ Restricted script access:
			§ Engineering scripts: Limited to the engineering group.
			§ Research scripts: Limited to the research group.
			§ Finance scripts: Limited to the finance group.
	5. User Management:
		○ Terminated Staff:
			§ Removed all terminated staff accounts and their associated home directories and files.
		○ Staff on Temporary Leave:
			§ Locked accounts for users on temporary leave.
		○ Employed Staff:
			§ Unlocked accounts for employed users.
		○ Marketing to Research Group:
			§ Moved all employees from the marketing group to the newly created research group.
			§ Removed the marketing group as it was no longer needed.
	6. Password Security:
		○ Updated password requirements in /etc/pam.d/common-password to meet security standards:

password requisite pam_pwquality.so retry=2 minlen=8 ucredit=-1 ocredit=-1
			§ Minimum 8 characters.
			§ At least one uppercase letter.
			§ At least one special character.
			§ Allow 2 retries for entering a password.
			
	7. Password hashing configuration:
		○ Updated the password hashing configuration to use SHA-512 hashing algorithm
		
	8. Sudo Privileges:
		○ Sherlock: The only user with full sudo privileges.
			§ Ensured all other users with full privileges were removed.
		○ Watson and Mycroft: Restricted sudo privileges to execute the following script:

/var/log/logcleanup.sh
		
		○ Research Group: Granted sudo privileges to all users in the research group to execute the following script:

/tmp/scripts/research_script.sh
		
	9. Automated Scripts:
		○ Created and validated:
			§ hardening_script1.sh: Performs system checks, backups, and permissions updates.
			§ hardening_script2.sh: Automates updates, logging checks, and reporting.
		○ Scheduled scripts using cron:
			§ Script 1: Runs monthly on the 1st of the month.
			§ Script 2: Runs weekly every Monday.

Summary of Security Concerns
During the hardening and auditing of the Linux environment, the following security concerns were identified and addressed:
	1. SSH Vulnerabilities:
		○ Issue: Root login and empty passwords allowed unauthorized access.
		○ Solution: SSH was restricted to non-root users with strong passwords and Protocol 2.
	2. Insecure Services:
		○ Issue: Legacy services (telnet, rsh-client) that transmit data unencrypted were detected.
		○ Solution: These services were removed.
	3. File Permissions:
		○ Issue: Files with world permissions posed risks of unauthorized access.
		○ Solution: World permissions were removed, and group-specific restrictions were implemented for critical scripts.
	4. User Management:
		○ Issue: Terminated staff accounts and users on temporary leave posed risks if not handled.
		○ Solution:
			§ Terminated staff accounts were deleted, including their files and home directories.
			§ Accounts of users on temporary leave were locked.
			§ Active employee accounts were unlocked as needed.
	5. Sudo Privilege Mismanagement:
		○ Issue: Multiple users had full sudo access, increasing the risk of privilege misuse.
		○ Solution:
			§ Only Sherlock retained full sudo privileges.
			§ Specific users and groups (Watson, Mycroft, and the research group) were granted restricted sudo access to execute designated scripts.
	6. Password hashing algorithm and Policy:
		○ Issue: Weak passwords posed a risk of brute-force attacks.
		○ Solution: Password requirements were enforced via /etc/pam.d/common-password, including:
			§ Minimum length: 8 characters.
			§ At least 1 uppercase letter and 1 special character.
			§ Limited retries to 2.
			§ password sufficient pam_unix.so sha512 
	7. Automation and Monitoring:
		○ Solution:
			§ Automated hardening and auditing tasks using scripts (hardening_script1.sh and hardening_script2.sh).
			§ Scheduled these scripts with cron for periodic execution.

Conclusion
By implementing these hardening and auditing tasks:
	• Unnecessary services were removed.
	• Password policies and hashing algorithm were strengthened to prevent weak passwords.
	• Sudo privileges were carefully restricted, ensuring the principle of least privilege.
	• User accounts were audited, with terminated users removed and temporary accounts locked.
	• File permissions were secured, restricting access to sensitive scripts.
	• Logging and automation were configured to ensure continuous monitoring and system integrity.
	
The system now adheres to security best practices, significantly reducing vulnerabilities and enhancing the overall security posture of the Linux environment.
