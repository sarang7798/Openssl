# Openssl
#File include some important command for OpenSSL OpenShift environment

oc new-project test

oc new-app --name=app1 --docker-image=httpd

oc get pod

oc create sa mysa

oc adm policy add-scc-to-user anyuid -z mysa

oc edit dc app1

oc get pod

oc get pod -w

oc get svc

curl 172.30.173.171

oc expose svc app1

oc get route

openssl genrsa -out private.key 2048

openssl req -new -key private.key -out example-ca.csr

openssl x509 -req -days 366 -in example-ca.csr -signkey private.key -out public.crt

oc get route

oc delete route app1

oc create route edge --service=app1 --hostname=app1-test.2886795332-80-simba02.environments.katacoda.com --key=private.key --cert=public.crt

oc get route
