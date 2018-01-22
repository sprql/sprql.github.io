---
layout:  post
title:   "TIL: iptables"
date:    2018-01-22 00:00:00 +0000
excerpt: ""
image:   ""
---

[serverfault.com](https://serverfault.com/a/578781):

    By making the firewall stateful and the first rule the typical 
    -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
    the vast majority of legitimate traffic to your server is 
    accepted after passing only that single rule. 
    That traffic doesn't need to traverse any other rules.    


The `netfilter-persistent` package from Debian is useful for save/restore rules.

When using [Ansible module to modify the systems iptables](http://docs.ansible.com/ansible/latest/iptables_module.html) - When `reject-with` used no need to add `jump=reject` because it will duplicate `-j` for iptables and throw an error; when using `!` for rules, use it whit quotes: `"!.."`


## Useful resources:

- [iptables(8) – Linux man page](https://linux.die.net/man/8/iptables) 
- [iptables rules from github.com/yeasy/best-practice](https://github.com/yeasy/best-practice/blob/master/security/iptables.rules)
- [Best practices: iptables](https://major.io/2010/04/12/best-practices-iptables/) by Major Hayden
