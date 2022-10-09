## Ansible tutorial

### Requirements

- ssh-keygen
- docker and [compose plugin](https://docs.docker.jp/compose/install/compose-plugin.html)
- python3 (required by ansible)
- [ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible)

### Setup

```bash
# Generate SSH Key pair
ssh-keygen -t rsa -b 2048 -f ./keys/bastion/id_rsa
docker compose build --build-arg ssh_public_key="$(cat ./keys/bastion/id_rsa.pub)"
docker compose up -d

# Test
ssh maintenance-user@192.168.49.100 -p 22222 -i ./keys/bastion/id_rsa
ansible demoservers -m ping -i inventory.yml -u maintenance-user
ansible-playbook -i inventory.yml playbook-bastion.yml
```

