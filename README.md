# service-discovery
How Kubernetes uses DNS for service discovery

```
[user@phatbox epick8s_class (⎈ |Epick8s:default)]$ kubectl run -i -t busybox --image=radial/busyboxplus:curl --restart=Never -- sh
If you don't see a command prompt, try pressing enter.
/ # nslookup helloworld-service.default.svc.cluster.local
Server:		10.0.0.10
Address:	10.0.0.10:53


*** Can't find helloworld-service.default.svc.cluster.local: No answer

/ # nslookup kubernetes.default.svc.cluster.local
Server:		10.0.0.10
Address:	10.0.0.10:53

Non-authoritative answer:
Name:	kubernetes.default.svc.cluster.local
Address: 10.0.0.1

*** Can't find kubernetes.default.svc.cluster.local: No answer

/ # ping helloworld-service
PING helloworld-service (10.0.36.224): 56 data bytes
^C
--- helloworld-service ping statistics ---
5 packets transmitted, 0 packets received, 100% packet loss
/ # nslookup 10.0.36.224
Server:		10.0.0.10
Address:	10.0.0.10:53

Non-authoritative answer:
224.36.0.10.in-addr.arpa	name = helloworld-service.default.svc.cluster.local
```
