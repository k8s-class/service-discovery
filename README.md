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

curl http://helloworld-service:31001
Hello World![ root@busybox:/ ]$ 

```
```nslookup kubernetes.default.svc.cluster.local
Server:    10.233.0.3
Address 1: 10.233.0.3 kube-dns.kube-system.svc.cluster.local

Name:      kubernetes.default.svc.cluster.local
Address 1: 10.233.0.1 kubernetes.default.svc.cluster.local
[ root@busybox:/ ]$ nslookup helloworld-v1.default.svc.cluster.local
Server:    10.233.0.3
Address 1: 10.233.0.3 kube-dns.kube-system.svc.cluster.local

Name:      helloworld-v1.default.svc.cluster.local
Address 1: 10.233.44.157 helloworld-v1.default.svc.cluster.local
[ root@busybox:/ ]$ curl http://10.233.44.157
<html>
This is my actual code
</html>[ root@busybox:/ ]$ curl http://helloworld-v1.default.svc.cluster.local
<html>
This is my actual code
</html>[ root@busybox:/ ]$ 
```
