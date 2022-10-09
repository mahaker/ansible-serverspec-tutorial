## Ansible tutorial

### Requirements

- ssh-keygen
- docker and [compose plugin](https://docs.docker.jp/compose/install/compose-plugin.html)

### Setup

```shell
# Generate SSH Key pair
ssh-keygen -t rsa -b 2048 -f ./keys/bastion/id_rsa
docker compose build --build-arg ssh_public_key="$(cat ./keys/bastion/id_rsa.pub)"
docker compose up -d

# Test
ssh maintenance-user@localhost -p 22222 -i ./keys/bastion/id_rsa
```

