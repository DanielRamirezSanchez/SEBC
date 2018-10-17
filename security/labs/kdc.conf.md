[daniramirez@SEBC-Cloudera-vm1 ~]$ sudo cat /var/kerberos/krb5kdc/kdc.conf

    default_realm = HADOOP.COM

    [kdcdefaults]
      kdc_ports = 88
      v4_mode = nopreauth

    [realms]
     HADOOP.COM = {
      kdc_ports = 88
      admin_keytab = /etc/kadm5.keytab
      database_name = /var/kerberos/krb5kdc/principal
      acl_file = /var/kerberos/krb5kdc/kadm5.acl
      key_stash_file = /var/kerberos/krb5kdc/stash
      max_life = 10h 0m 0s
      max_renewable_life = 7d 0h 0m 0s
      master_key_type = des3-hmac-sha1
      supported_enctypes = arcfour-hmac:normal des3-hmac-sha1:normal des-cbc-crc:normal des:normal des:v4 des:norealm des:onlyrealm des:afs3
      default_principal_flags = +preauth
      #master_key_type = aes256-cts
      #dict_file = /usr/share/dict/words
      supported_enctypes = aes256-cts:normal aes128-cts:normal des3-hmac-sha1:normal arcfour-hmac:normal camellia256-cts:normal camellia128-cts:normal des-hmac-sha1:normal des-cbc-md5:normal des-cbc-crc:normal
     }
