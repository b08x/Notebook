## create macvlan connection

```bash
sudo nmcli connection edit
```
```
nmcli> set macvlan.parent eno1
nmcli> set macvlan.mode bridge
nmcli> set ipv4.addresses 192.168.41.40/28
nmcli> set connection.interface-name shim
nmcli> save
nmcli> activate
```

## open up the required ports

```bash
sudo firewall-cmd --add-service=dns --permenant
sudo firewall-cmd --add-service=dhcp --permenant
sudo firewall-cmd --add-service=http --permenant
sudo firewall-cmd --add-service=https --permenant
sudo firewall-cmd --reload
```

## create docker network

```bash
docker network create -d macvlan -o parent=eno1 \
--subnet 192.168.41.0/24 --gateway 192.168.41.1 \
--ip-range 192.168.41.40/28 \
--aux-address 'host=192.168.41.40' \
macvlan0
```

## create docker-compose file

```yaml
---
version: '3.8'

services:
  pihole:
    container_name: pihole-container
    image: pihole/pihole:latest # check the latest version on docker hub.
    hostname: pihole # set an easy hostname to remember
    domainname: syncopated.net # your local domain name
    mac_address: de:ad:be:ef:ff:01 # can change or leave this??
    cap_add:
      - NET_ADMIN
    networks:
      macvlan0: # same as network specified below
        ipv4_address: 192.168.41.41 # the IP of the pihole container
    dns:
      - 127.0.0.1 # use local DNS, since the pihole
      - 8.8.8.8 # optional fallback DNS
    volumes: # mount our data volumes.
       - './etc-pihole/:/etc/pihole/'
       - './etc-dnsmasq.d/:/etc/dnsmasq.d/'
       - './backups/:/backups/' # backups explained later
    environment: # set variables for pihole configuration.
      ServerIP: 192.168.41.41 # must match ipv4_address above
      VIRTUAL_HOST: pihole.syncopated.net  # Must be hostname + domainname from above
      WEBPASSWORD: "randompassword"
      TZ: 'America/New_York' # pick your timezone
    restart: unless-stopped

networks:
  macvlan0:
    external: true

```


- [ ] fail over⏫ 

---


# alternatively??

```yaml
version: '3.9'

services:
    pihole:
       image: pihole/pihole:latest
       container_name: pihole
       ports:
           - "8090:80"
       environment:
          - WEBPASSWORD=adminpassword
          - TZ=America/New_York
          - DNSSEC=True
          - PUID=1000
          - PGID=1000
          - VIRTUAL_HOST=pihole
       volumes:
          - ./etc/pihole:/etc/pihole
          - ./etc/dnsmasq:/etc/dnsmasq.d
       cap_add:
          - NET_ADMIN
       dns:
          - 127.0.0.1
          - 8.8.8.8
          - 4.4.4.4
       networks:
         network:
           ipv4_address: 10.5.0.2

networks:
  network:
    driver: bridge
    ipam:
      config:
        - subnet: 10.5.0.0/16
          gateway: 10.5.0.1

```

Then add a cname for the dockerhost in `Additional DNSMasq Options`

[source](https://blog.ivansmirnov.name/set-up-pihole-using-docker-macvlan-network/)


