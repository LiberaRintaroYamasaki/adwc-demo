# adwc-demo
Object StorageからADWCへデータロードをする

You can download [sample data](https://console.us-ashburn-1.oraclecloud.com/object-storage/buckets/liberarintaro/BucketForDemo).

## Load Data - Create Credentials and Copy Data into an Existing Table

Access the notebook.

#### create credential
```
%script
BEGIN
    DBMS_CLOUD.CREATE_CREDENTIAL(
        credential_name => '',
        username => '',
        password => ''
    );
END;
/
```

#### create table
```
%sql
CREATE TABLE CHANNELS
   (channel_id char(1),
    channel_desc varchar2(20),
    channel_class varchar2(20)
   );

/
```


#### load data into an existing table  
```
%sql
BEGIN
 DBMS_CLOUD.COPY_DATA(
    table_name =>'CHANNELS',
    credential_name =>'DEF_CRED_NAME',
    file_uri_list =>'https://objectstorage.us-phoenix-1.oraclecloud.com/n/adwc/b/adwc_user/o/channels.txt',
    format => json_object('delimiter' value ',')
 );
END;
/
```









