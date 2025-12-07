#download the curresponding ipa-server https://access.redhat.com/downloads/content/rhel---7/x86_64/2456/ipa-server/4.1.0-18.el7_1.4/x86_64/fd431d51/package<br>

| Field                   | Value                                            |
| ----------------------- | ------------------------------------------------ |
| Vendor                  | **Red Hat Directory Server**                     |
| Connection URL          | `ldaps://ipa.lab.local:636`                      |
| Bind DN                 | `uid=admin,cn=users,cn=accounts,dc=lab,dc=local` |
| Bind Credential         | FreeIPA admin password                           |
| Users DN                | `cn=users,cn=accounts,dc=lab,dc=local`           |
| Edit Mode               | READ_ONLY                                        |
| Username LDAP attribute | uid                                              |
| RDN LDAP attribute      | uid                                              |
| UUID LDAP attribute     | ipaUniqueID                                      |
| Use Truststore SPI      | Only for ldaps                                   |

#create users<br>ipa user-add testuser \
 --first=Test \
 --last=User \
 --password
