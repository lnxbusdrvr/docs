# Manually setting gateway-address with route-command #
**Syntax:**
```bash
route add default gw <gateway-address>
```
**eg:**
```bash
route add default gw 192.168.0.1
```
### Setting other route ###
**Syntax:**
```bash
route add -net network <network-address> netmask <netmaskaddress> gw <gateway-address>
```
**eg:**
```bash
route add -net network 15.0.0.0 netmask 255.0.0.0 gw 10.0.0.252
```
### Deleting the route
**Syntax:**
```bash
route del -net network <network-address> netmask <netmaskaddress> gw <gateway-address>
```
**eg:**
```bash
route add -net network 15.0.0.0 netmask 255.0.0.0 gw 10.0.0.252
```
