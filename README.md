Deploy Using Helm 


<!-- Add the Helm repo: -->


helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update


<!-- Create the namespace: -->


kubectl create namespace monitoring


<!-- Install the chart: -->


helm upgrade --install kube-prometheus-stack prometheus-community/kube-prometheus-stack \
  -n monitoring -f kube-prometheus-stack/values.yaml


<!-- ✅ Add Ingress DNS Entries
If testing locally, update /etc/hosts: -->


<INGRESS_CONTROLLER_IP> prometheus.erickyc.store grafana.erickyc.store
Find the IP with:

kubectl get svc -n ingress-nginx