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

oc apply -f dc.yaml

oc get pods ---> wait for deploy pod to be completed. Wait for app pod to be running.

Verify storage /mnt/pv-data/sridhar

ssh -i ~/.crc/machines/crc/id_rsa core@192.168.64.11
cd /mnt
sudo ls -la /pv-data/sridhar

oc rsh myflaskapp-old-1-hp8nv (replace app pod name) to get access to pod and verify /new-sridhar directory.

