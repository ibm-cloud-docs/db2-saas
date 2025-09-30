---

copyright:
  years: 2014, 2021
lastupdated: "2025-09-30"

keywords:

subcollection: db2-saas

---


{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Federation - SSL from cloud to cloud database
{: #fedv2_cld_to_cld}

Federation allows you to communicate with one or more local or remote databases.

The following steps are required to configure the federation system:

1. [Database and host name layout](#fedv2_db_hn)
1. [Create the wrapper](#fedv2_wrapper)
1. [Create the server for a remote database](#fedv2_serv_remote_db)
1. [Create the user mapping](#fedv2_user_map)
1. [Create a nickname](#fedv2_nick)

{: .important}
**Important:** Federation between Classic and Performance instances requires public endpoints with allowlists. Private endpoints are not supported between these instance types. All Performance instances in a region share the same outbound IP, so traffic must be within IBM networks.

## Database and host name layout
{: #fedv2_db_hn}

Target database where the remote table must show:
```
Hostname :               <target_host_name>
DB2 Version:             v11.5
Database Name:           BLUDB
Schema Name:             <schema_name>
```

Remote database where the table is present:
```
Hostname :              <remote_host_name>
DB2 Version:            v11.5
Service/Port Number:    <port>
User:                   <remote_user>
Password:               <remote_password>
Database Name:          BLUDB
Schema Name:            TESTDB
Table Name:             TEST1
```

## Create a wrapper
{: #fedv2_wrapper}

Create a wrapper by running the following command from the console of the target database instance:
```
create wrapper drdawrapper library 'libdb2drda.so' options(DB2_FENCED 'Y')
```
{: codeblock}
```
DB20000I  The SQL command completed successfully.
```

## Create the server for a remote database
{: #fedv2_serv_remote_db}

Create a server to host the remote database by running the following command from the console of the target database instance:

### For Performance instances
```
create server fed_server type DB2/UDB version 12 wrapper drdawrapper authorization \"<remote_user>\" PASSWORD \"<remote_password>\" options(host '<remote_host_name>', port '<port>', dbname 'bludb', security 'SSL', password 'y')
```
{: codeblock}

### For Classic instances
```
create server fed_server type DB2/UDB version 11 wrapper drdawrapper authorization \"<remote_user>\" PASSWORD \"<remote_password>\" options(host '<remote_host_name>', port '<port>', dbname 'bludb', security 'SSL', password 'y')
```
{: codeblock}

{: .important}
**Important:** If you encounter SQL0104N errors, use escaped double quotes (\") for the authorization and PASSWORD parameters as shown above.
```
DB20000I  The SQL command completed successfully.
```

## Create the user mapping
{: #fedv2_user_map}

Create the user mapping by running the following command from the console of the target database instance:
```
create user mapping for user server fed_server OPTIONS (remote_authid '<remote_user>', remote_password '<remote_password>')
```
{: codeblock}
```
DB20000I  The SQL command completed successfully.
```

## Create a nickname
{: #fedv2_nick}

Create a nickname for the remote database and test the nickname by running the following commands from the console of the target database instance:
```
create nickname rmttest1 FOR fed_server.testdb.test1
```
{: codeblock}
```
DB20000I  The SQL command completed successfully.
```
```
select * from rmttest1
```
{: codeblock}
```
C1          C2
----------- -----------
         13          32

1 record(s) selected.
```
