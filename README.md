# Introduction
## Check Syntax

Add syntax checking by appending --syntax-check

    ansible-playbook playbook.yaml --syntax-check

## Add Host Inventory
vi hosts-list

    [testing_host]
    demo.exmple.com
    [todo_host]
    demo.example.com
    demo2.example.com
    demo3.example.com
    [finish]

-i target host file list

    ansible-playbook -i hosts-list playbook.yml

# Run Ansible Sample
## Execute Playbook
- Disable first time connection checking, then run the playbook with **SSH password prompt**.

```
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook -i host-list ansible/playbook.yml -b -v -K -k
```

 -i INVENTORY, --inventory INVENTORY, --inventory-file INVENTORY specify inventory host path or comma separated host list. --inventory-file is deprecated

-b, --become           run operations with become(sudo) (does not imply password prompting)

-v, --verbose           verbose mode (-vvv for more, -vvvv to enable connection debugging)

-K, --ask-become-pass   ask for privilege escalation password

-k, --ask-pass          ask for connection password



- Alternate Method
Disable first time connection checking, then run the playbook with **SSH private key**.

```
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook -i host-list ansible/playbook.yml -b -v -K --private-key=~/.ssh/id_rsa
```

  

# Remove User
    export ANSIBLE_HOST_KEY_CHECKING=False
    ansible-playbook -i host-list ansible-remove-user/playbook.yml -b -v -K -k
or

```
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook -i host-list ansible-remove-user/playbook.yml -b -v -K --private-key=~/.ssh/id_rsa
```

