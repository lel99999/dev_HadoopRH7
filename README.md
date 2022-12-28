# dev_HadoopRH7
Hadoop Workspace with RHEL 7

##### HDP Review
- Ambari SSL Configuration
  - [https://docs.cloudera.com/HDPDocuments/Ambari-2.2.1.1/bk_Ambari_Security_Guide/content/_optional_set_up_ssl_for_ambari.html](https://docs.cloudera.com/HDPDocuments/Ambari-2.2.1.1/bk_Ambari_Security_Guide/content/_optional_set_up_ssl_for_ambari.html) <br/>
  - [https://docs.cloudera.com/HDPDocuments/Ambari-2.2.1.1/bk_Ambari_Security_Guide/content/_set_up_truststore_for_ambari_server.html](https://docs.cloudera.com/HDPDocuments/Ambari-2.2.1.1/bk_Ambari_Security_Guide/content/_set_up_truststore_for_ambari_server.html) <br/> 

- Repos: HDP-2.x, HDP-UTILS-1.10.22, AMBARI

  - Errors & Fixes:
    - Agent Registration issues
      - /etc/hosts - <IP> <FQDN> <SYSNAME> <br/>
        ```
        $hostname -f
        $hostnamectl set-hostname <FQDN>
        ```
      - SSL certificate verification in Python Std Library HTTP Clients
        In /etc/ambari-agent/conf/ambari-agent.ini <br/>
        ```
        [security]
        force_https_protocol=PROTOCOL_TLSv1_2
        ``` 

      - RHEL 7.x requires libtirpc-devel  <br/>
        ```
        $sudo subscription-manager repos --enable=rhel-7-server-optional-rpms
        $sudo yum install -y libtirpc-devel
        ```
    - Hive Metastore deployment/start error
      - Get mysql/postgresql (mysql-connector-java.jar) copy to /var/lib/ambari-agent/tmp
        
#### Ambari Synchronizing LDAP Users & Groups
- [https://docs.cloudera.com/HDPDocuments/HDP3/HDP-3.0.1/ambari-authentication-ldap-ad/content/authe_ldapad_synchronizing_ldap_users_and_groups.html](https://docs.cloudera.com/HDPDocuments/HDP3/HDP-3.0.1/ambari-authentication-ldap-ad/content/authe_ldapad_synchronizing_ldap_users_and_groups.html) <br/>
  ```
  $ambari-server sync-ldap --users users.txt --groups groups.txt
  ```
