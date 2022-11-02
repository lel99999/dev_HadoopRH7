# dev_HadoopRH7
Hadoop Workspace with RHEL 7

##### HDP Review
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
        
