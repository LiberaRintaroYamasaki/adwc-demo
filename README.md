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
CREATE TABLE airbnb
    (Host_Id number(10),
     Host_Since date,
     Name varchar2(100),
     Neighbourhood varchar2(20),
     Review_Scores_Rating_Bin number(10),
     Room_Type varchar2(20),
     Zipcode number(5),
     Beds number(2),
     Number_of_Records number(2),
     Number_Of_Reviews number(4),
     Price number(6),
     Review_Scores_Rating number(3)
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









