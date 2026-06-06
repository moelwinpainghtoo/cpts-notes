
```bash
# Brute force c string with onesixtyone & Found info from SNMP
Admin <tech@inlanefreight.htb>
iso.3.6.1.2.1.25.1.7.1.2.1.2.6.66.65.67.75.85.80 = STRING: "/opt/tom-recovery.sh"
iso.3.6.1.2.1.25.1.7.1.2.1.3.6.66.65.67.75.85.80 = STRING: "tom NMds732Js2761"

# Login to mail server via IMAP
Found an email in INBOX containing Private Key of user tom

# SSH to server
Found tom is part of mysql group
Login to Mysql via tom creds found from SNMP and get creds
```