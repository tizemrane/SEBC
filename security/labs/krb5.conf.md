```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = SEBC.COM
 dns_lookup_realm = false
 dns_lookup_kdc = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true

[realms]
 SEBC.COM = {
  kdc = n1.sebcdomain
  admin_server = n1.sebcdomain
 }

[domain_realm]
 .sebcdomain = SEBC.COM
 sebcdomain = SEBC.COM
```