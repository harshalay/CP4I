# CP4I

### Login to the OpenShift cluster 
```oc login```

### Create a new project 
```oc new-project PROJECT_NAME (oc new-project cp4i)```

## MQ

### Create tis key and certificate

### [MQ](https://developer.ibm.com/tutorials/mq-secure-msgs-tls/)

create the server key and certificate 
```openssl req -newkey rsa:2048 -nodes -keyout key.key -x509 -days 365 -out key.crt```

Verify that the certificate has been created successfully
```openssl x509 -text -noout -in key.crt```

To create a .jks client keystore and import our sever certificate into it
```keytool -keystore clientkey.jks -storetype jks -importcert -file key.crt -alias server-certificate```


