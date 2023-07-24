
# Run this
```
iptables -A FORWARD -i eth0 -o lxdbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i lxdbr0 -o eth0 -j ACCEPT
iptables-save
```
# if still not working Run this extra rule
```
iptables -t nat -A POSTROUTING -s <your-lxd-network>/24 -o lxdbr0 -j MASQUERADE
iptables-save
```
