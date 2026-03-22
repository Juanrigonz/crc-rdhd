# 1. Extrae el certificado maestro del router y lo guarda en un archivo
oc get configmap default-ingress-cert -n openshift-config-managed -o jsonpath='{.data.ca-bundle\.crt}' > crc-ca.crt

# 1. Extrae el certificado maestro del router y lo guarda en un archivo
oc get configmap default-ingress-cert -n openshift-config-managed -o jsonpath='{.data.ca-bundle\.crt}' > crc-ca.crt

openssl s_client -showcerts -connect keycloak.apps-crc.testing:443 </dev/null 2>/dev/null | sed -n -e '/BEGIN\ CERTIFICATE/,/END\ CERTIFICATE/ p' > crc-ca.crt
juangonz@juangonz-thinkpadp1gen7:~/Downloads/kafka-proxy-envio/producer-app$ oc create configmap crc-router-ca --from-file=ca.crt=crc-ca.crt -n rhdh-operator


