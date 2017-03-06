### 配置Ambari管理Kerberos鉴权

ambari-server setup-security

[https://community.hortonworks.com/articles/42927/adding-kdc-administrator-credentials-to-the-ambari.html](https://community.hortonworks.com/articles/42927/adding-kdc-administrator-credentials-to-the-ambari.html)



During the process of enabling Kerberos via Ambari's web-based UI, the user is prompted for this information and has the option to store the credentials in either the_**temporary**_or_**persisted**_credential store. The_**temporary**_credential store is a keystore in memory where each entry is removed after 90 minutes \(from initial creation\), when Ambari is restarted, or by user request. The_**persisted**_credential store is a keystore stored on disk where each entry is removed only by user request.**The option to store a credential in the**_**persisted**_**store is only available if Ambari's credential store has been setup.**





**Creating Ambari's Credential Store**

To set up Ambari's credential store, the following commands must be invoked from the Ambari server host's command line:

```

```

**Option \#2**, "Encrypt passwords stored in ambari.properties file", is then used to start the process:

Example:

```

```

Once this is complete, the Ambari credential store will be located at**/var/lib/ambari-server/keys/credentials.jceks**.

To test the password entered when creating the credential store, you can issue the following command:

```

```

Where $JAVA\_HOME is the path to where Java is installed. For example,**/usr/jdk64/jdk1.8.0\_60**.

Example:

```

```

Note that this is optional if there is no need to persist the KDC administrator credentials. However, if opting to create Ambari's credential store, other passwords typically stored in plaintext in Ambari's properties file \(**/etc/ambari/conf/ambari-server.properties**\) will be encrypted and stored in the created credential store.



**Restarting Ambari**

After this has been set up, Ambari**must**be restarted in order for it to acquire the new information about the credentials store. If Ambari**was stopped**before setting up the credential store, it must be started.

```

```

If Ambari**was**_**not**_**stopped**before setting up the credential store, it must be restarted.

```

```



