# openshiftappyaml

oc create namespace myproject

oc project myproject

oc apply -f is.yaml

oc apply -f bc.yaml

oc get pods ---> wait for build pod to be completed.

oc logs myflaskapp-old-2-build   ---> to view build logs progress until push successful.Note image registry url (from Successfully pushed image-registry......... line in the log output).

Edit dc.yaml and update image registry entry under spec -> template -> spec -> containers.

oc apply -f pv.yaml

oc apply -f pvc.yaml

oc apply -f secret.yaml

note: secret.yaml has encoded data. These were encoding using base64. 

$base64 <<< <data in plaintext>
<encoded data is returned>
  
$base64 -D <<< <data in encoded format>
<plaintext data is returned>

oc apply -f cm.yaml

oc apply -f dc.yaml

oc get pods ---> wait for deploy pod to be completed. Wait for app pod to be running.

Verify storage /mnt/pv-data/sridhar

ssh -i ~/.crc/machines/crc/id_rsa core@192.168.64.11
cd /mnt
sudo ls -la /pv-data/sridhar

oc rsh myflaskapp-old-1-hp8nv (replace app pod name) to get access to pod and verify /new-sridhar directory.

And also check this inside pod:

(app-root) sh-4.2$ printenv | grep "OS_"

OS_PROJECT_NAME=project

OS_DOMAIN_NAME=domain

OS_AUTH_URL=https://127.0.0.1:8000

OS_CACERT_DATA=certdata

OS_CACERT=/etc/config/openstack.crt

(app-root) sh-4.2$ 

(app-root) sh-4.2$ echo $username

user-name

(app-root) sh-4.2$ echo $password

password

(app-root) sh-4.2$ 

