# Peaq Technology GmbH Ansible playbooks for ssh key management

## Add new user and grant SSH access
`ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml`

## Grant SSH access to an existing user
`ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml --skip-tags=add`

## Revoke SSH access from a user
`ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml --skip-tags=remove`

## Revoke and remove user
`ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml`

## variables

inventory/hosts file contains group [instances] put your target hosts here

[instances:vars] have 2 parameters: 
- `user_name` (user to be operated, also you need to create directory `sshkeys/$user_name` and put keys there)
- `user_des` (detailed information about this user)

You MUST put appropriate user under remote_user in `playbooks/ssh.yml` (this user MUST have access to target services and have passwordless access to target hosts from your machine)
