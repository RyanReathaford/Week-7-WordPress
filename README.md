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
2. Username scrape and Brute force attack
  - [ ] Summary: 
    - Vulnerability types: Scrape Usernames and Brute Force password
    - Tested in version: 4.2
    - Fixed in version: None
  - [ ] GIF Walkthrough: https://imgur.com/a/iNAQB 
  - [ ] Steps to recreate: 
	- The attacker can use the wpscan tool in Kali Linux to scrape a list of usernames with the command:
	- wpscan -u url of wordpress site --enumerate u Example: wpscan -u wpdistillery.vm -- enumerate u
	- This returns a list of user accounts for this specific site
	- Next the attacker can use a wordlist along with a username to brute force the password with command:
	- wpscan -u url of wordpress site -- username pick a listed username --wordlist path of wordlist
		- example: wpscan -u wpdistillery.vm --username admin --wordlist /root/Desktop/Passwords
  - [ ] Affected source code:
	- This is not due to source code, but is a combination of weak passwords and no maximum attempts restriction on logins
3. (Required) Authenticated Shortcode Tags Cross-Site Scripting
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.3.1
  - [ ] GIF Walkthrough: https://imgur.com/a/chQwP
  - [ ] Steps to recreate: 
	- The attacker must have posting access to the WP page.
	- Create or modify a post or page
	- Using the text editer to insert code similar to 
		- [caption width="1" caption='/\<a href="' ">]/\</a>/\<a href=" \<event attribute with JS code> ">Dont Click!\</a>
	- I went with
		- [caption width="1" caption='\<a href="' ">]\</a>\<a href=" onmouseover='alert("Congratulations, you played yourself!")' ">Dont Touch!\</a>
- [Link 1](https://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/)
## Resources
https://www.cvedetails.com/vulnerability-list/vendor_id-2337/product_id-4096/
https://www.youtube.com/watch?v=9tLUbsdNX88
##Assets
I used Kali linux and WPScan
## Notes
Some challenges that I ran into involved the JS code as I am not a strong coder.  I also had a lot of problems getting everything to run correctly in the lab challenges.  I had to delete everything and start over several times.  
## License

    Copyright [2018] [Gary Reathaford]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
