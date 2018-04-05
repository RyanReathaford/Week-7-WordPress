# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. CVE 2015-5622: Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: https://imgur.com/a/XcQWU
  - [ ] Steps to recreate: 
	- A user must have contribute permissions to begin the exploit
	- The attacker must then try to create a comment or post
	- Using the Text editer (not the visual) in the post box the user can insert code such as:
	- \<a href="[caption code=">]\</a>\<a title=" onmouseover=alert('XSS!')  ">Click here to win a prize link.\</a>\
	-While this just popped up a simple alert, an attacker could hide far more malicoius code.
  - [ ] Affected source code: 
    - [Link 1](https://core.trac.wordpress.org/changeset/33359)
1. Username scrape and Brute force attack
  - [ ] Summary: 
    - Vulnerability types: Scrape Usernames and Brute Force password
    - Tested in version: 4.2
    - Fixed in version: None
  - [ ] GIF Walkthrough: https://imgur.com/a/iNAQB 
  - [ ] Steps to recreate: 
	- The attacker can use the wpscan tool in Kali Linux to pull a list of username with the command:
	- wpscan -u url of wordpress site --enumerate u Example: wpscan -u wpdistillery.vm -- enumerate u
	- This returns a list of user accounts for this specific site
	- Next the attacker can use a wordlist along with a username to brute force the password with command:
	- wpscan -u url of wordpress site -- username pick a listed username --wordlist path of wordlist
		- example: wpscan -u wpdistillery.vm --username admin --wordlist /root/Desktop/Passwords
  - [ ] Affected source code:
	- This is not due to source code, but is a combination of weak passwords and no maximum attempts restriction on logins
