# Configuration for dokuwiki

LDAP configuration is in ```/dokuwiki/conf/local.protected.php```:

```
<?php
$conf['useacl']         = 1;           //enable ACL
$conf['authtype']       = 'authldap';  //enable this Auth plugin
$conf['plugin']['authldap']['server']      = 'ldap://lldap_server:3890'; #IP of your lldap
$conf['plugin']['authldap']['usertree']    = 'ou=people,dc=example,dc=com';
$conf['plugin']['authldap']['grouptree']   = 'ou=groups, dc=example, dc=com';
$conf['plugin']['authldap']['userfilter']  = '(&(uid=%{user})(objectClass=person))';
$conf['plugin']['authldap']['groupfilter'] = '(&(objectClass=group)(memberUID=member))';
$conf['plugin']['authldap']['attributes']  = array('cn', 'displayname', 'mail', 'givenname', 'objectclass', 'sn', 'uid', 'memberof');
$conf['plugin']['authldap']['version']    = 3;
$conf['plugin']['authldap']['binddn']     = 'cn=admin,ou=people,dc=example,dc=com';
$conf['plugin']['authldap']['bindpw']     = 'ENTER_YOUR_LLDAP_PASSWORD';
```

DokuWiki by default, ships with an LDAP Authentication Plugin called ```authLDAP``` that allows authentication against an LDAP directory.
All you need to do is to activate the plugin. This can be done on the DokuWiki Extensions Manager.

Once the LDAP settings are defined, proceed to define the default authentication method.
Navigate to Table of Contents > DokuWiki > Authentication.
On the Authentication backend, select ```authldap``` and save the changes.
