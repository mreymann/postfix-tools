# postfix-tools :envelope::wrench:

Tools that might be of use for administrators of the Postfix MTA.

## plainmails-in / plainmails-out :unlock:

List of MX hosts that don't use TLS encryption when sending / receiving mails.

### Prerequesites

These scripts use plain PHP, so only the CLI package is needed:

* yum install php-cli (CentOS)
* apt install php-cli (Ubuntu)

The scripts expect to read your mail log from STDIN.

### Examples

```
$ cat /var/log/maillog | plainmails-in
Incoming mail count (total 3636):
---------------------------
3582    using TLS
54      unencrypted (1 %)

Top 5 unencrypted MX hosts:
---------------------------
6       smtp.example.com (123.123.254.69)
6       mail.example.com (123.123.157.202)
3       web01.example.com (123.123.24.35)
3       example.com (123.123.191.242)
3       xtc01.foo.example.com (123.123.110.11)
```
Same for outgoing:
```
$ cat /var/log/maillog | plainmails-out
Outgoing mail count (total 73617):
---------------------------
72803   using TLS
814     unencrypted (1 %)

Top 5 unencrypted MX hosts:
---------------------------
699     mailgw.example.com (123.123.15.193)
28      mx2.example.com (123.123.192.10)
14      mailgw2.example.com (123.123.15.193)
13      mail.example.com (123.123.88.254)
10      mail3.example.com (123.123.191.242)
```
