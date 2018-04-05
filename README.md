# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Vulnerability Name or ID
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
