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

1. Add a secret with the private and public key ```oc apply -f mq-tls-secret.yaml```
2. Add the MQSC commands to a ConfigMap.```oc apply -f mq-mqsc-configmap.yaml```
3. Create the Queue Manager using the certificates and MQSC commands from the previous steps by running the command ```oc apply -f nativeHA.yaml```
4. To allow the Queue Manager to be contact outside of the OCP environment update the channel name with ```external2e-svrconn.chl.mq.ibm.com``` then apply the changes ```oc apply -f mq-route.yaml```
