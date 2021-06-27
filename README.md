# Vagrant + Consul + Vault

## Usage

### Installation

```
vagrant up
```

### Configuration

server1

```
vagrant ssh server1

consul agent \
  -server \
  -bootstrap-expect=1 \
  -node=agent-one \
  -bind=10.1.142.101 \
  -data-dir=/tmp/consul \
  -config-dir=/etc/consul.d

consul members
```

server2

```
vagrant ssh server2

consul agent \
  -node=agent-two \
  -bind=10.1.142.102 \
  -enable-script-checks=true \
  -data-dir=/tmp/consul \
  -config-dir=/etc/consul.d
```

server3

```
vagrant ssh server3

consul agent \
  -node=agent-three \
  -bind=10.1.142.103 \
  -enable-script-checks=true \
  -data-dir=/tmp/consul \
  -config-dir=/etc/consul.d
```

client1

```
vagrant ssh client1

vault server -dev -config /etc/vault.d/configuration.hcl
```

client2

```
vagrant ssh client2

vault server -dev -config /etc/vault.d/configuration.hcl
```

## License

MIT
