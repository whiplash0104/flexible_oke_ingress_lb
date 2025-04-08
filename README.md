Para crear un Ingress Controller Nginx LB en una subred privada, descargar yaml de ingress controller en base a la docuembtación
https://docs.oracle.com/en-us/iaas/Content/ContEng/Tasks/contengsettingupingresscontroller.htm

Y editar el archivo, en el servicio y agregar annotations

**annotations:** 

  **service.beta.kubernetes.io/oci-load-balancer-internal: "true"**
  
  **service.beta.kubernetes.io/oci-load-balancer-subnet1: 'ocid1.subnet.oc1.XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'**

```
apiVersion: v1
kind: Service
metadata:
  labels:
    app.kubernetes.io/component: controller
    app.kubernetes.io/instance: ingress-nginx
    app.kubernetes.io/name: ingress-nginx
    app.kubernetes.io/part-of: ingress-nginx
    app.kubernetes.io/version: 1.11.3
  annotations:
    service.beta.kubernetes.io/oci-load-balancer-internal: "true"
    service.beta.kubernetes.io/oci-load-balancer-subnet1: 'ocid1.subnet.oc1.XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
  name: ingress-nginx-controller
  namespace: ingress-nginx
```
