# k8s-cni-demo

## bash-cni配置

```
yum install curl jq nmap iproute2

sudo brctl addbr cni0
sudo ip link set cni0 up
sudo ip addr add <bridge-ip>/24 dev cni0 # bridge-ip: 172.20.0.1

# 0.3.1版本
cp bash-cni/10-bash-cni-plugin.conf /etc/cni/net.d/10-bash-cni-plugin.conf

cp bash-cni/bash-cni /usr/local/bin/bash-cni
systemctl restart kubelet
```

## TroubleShooting

```
service docker stop
service kubelet stop
reboot -f
```

## 参考链接

- [cni spec](https://github.com/containernetworking/cni/blob/master/SPEC.md)
- [https://www.altoros.com/blog/kubernetes-networking-writing-your-own-simple-cni-plug-in-with-bash/](https://www.altoros.com/blog/kubernetes-networking-writing-your-own-simple-cni-plug-in-with-bash/)