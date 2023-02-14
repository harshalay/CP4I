# CP4I

login to the OpenShift cluster oc login
create a new project oc new-project PROJECT_NAME (oc new-project cp4i)
Get your entitlement key (https://myibm.ibm.com/products-services/containerlibrary)
Store the entitlement key from the previous step in a secret oc create secret docker-registry ibm-entitlement-key --docker-server=cp.icr.io --docker-username=cp --docker-password=ENTITLEMENT_KEY --docker-email=OCP_LOGIN_CREDENTIALS
Connect to the IBM Docker Catalog and install the necessary operators using the command oc apply -f CP4IInstalaltion.yaml
