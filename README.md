# istio-practice

### Install the istioctl

Download the latest version of istioctl from releases

https://github.com/istio/istio/releases/

```
wget https://github.com/istio/istio/releases/download/1.14.1/istioctl-1.14.1-linux-amd64.tar.gz
```

Extarct the tar file

```
tar -xvzf istioctl-1.14.1-linux-amd64.tar.gz
```

```
chmod +x istioctl
mv istioctl /usr/local/bin/
```

Check the istioctl version

```
istioctl version
```

Download the istio from releases

https://github.com/istio/istio/releases/


```
wget https://github.com/istio/istio/releases/download/1.14.1/istio-1.14.1-linux-amd64.tar.gz
```

Extract the tar

```
tar -xvzf istio-1.14.1-linux-amd64.tar.gz
```

Install the demo profile

```
istioctl install --set profile=demo -y
```

Add label to default namespace

```
kubectl label namespace default istio-injection=enabled
```

Deploy the sample application

```
kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
```

```
kubectl get services
```

```
kubectl get pods
```

Verify the application

```
kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"
<title>Simple Bookstore App</title>
```


Enable the Ingress gateway

```
kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
```

Ensure that there are no issues with the configuration

```
istioctl analyze
```


Reference:

https://istio.io/latest/docs/setup/getting-started/



