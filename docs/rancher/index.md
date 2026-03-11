### Rancher

```bash
# если kubectl не работает, т.к. kubectl лежит не в стандартном /usr/local/bin, а во внутреннем каталоге Rancher
sudo ln -s /var/lib/rancher/rke2/bin/kubectl /usr/local/bin/kubectl

# Ready, значит ядро кластера в порядке
kubectl get nodes

# Проверка Rancher (должен быть 1/1 READY)
sudo kubectl --kubeconfig ~/.kube/config get pods -n cattle-system

# Проверка Ingress (должен быть статус Running)
sudo kubectl --kubeconfig ~/.kube/config get pods -n ingress-nginx

# Все поды в longhorn-system должны быть Running
sudo kubectl --kubeconfig ~/.kube/config get pods -n longhorn-system

# Проверка оператора KubeVirt
sudo kubectl --kubeconfig ~/.kube/config get pods -n kubevirt

# Проверка CDI (импортер образов)
sudo kubectl --kubeconfig ~/.kube/config get pods -n cdi

# Проверь реальные порты Ingress
kubectl get svc -n ingress-nginx
```