# New Server role.

This role is used for create the prerequesite for the other ansibles playbook from [my github.](https://git.luclis.xyz/LUCLIS-Admins/PROTO_Server)
In Ansible 2.10, it needs the [ansible.posix.authorized_key](https://docs.ansible.com/ansible/latest/collections/ansible/posix/authorized_key_module.html). In order to install it, you just need to run the following command.
```bash
ansible-galaxy collection install ansible.posix
```

## variables :
The defaults settings are :  
`ansible_user: user-ansible`                                    ==> The user who runs the other playbooks.  
`sudo_group: sudo`                                              ==> The sudo group.  
`git_url: "https://git.luclis.xyz/LUCLIS-Admins/PROTO_Server/"` ==> The URL of the github repository.  
`git_public_path:"Public/"`                                     ==> The Path where you'll fetch your public key for ssh connexion.  
`ssh_port:       "22"                                           ==> Your default port for ssh (server & client).  
`ssh_listen_ip:  "0.0.0.0"``                                    ==> Your default listening ip for ssh.  
`ssh_listen_ip6: "::"`                                          ==> Your default listening ip 6 for ssh.  
`ssh_root_login: "prohibit-password"`                          ==> Select if you want to connect in root with/without password or not.  
`ssh_chiphers:   "chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com"`  
`ssh_kex:        "curve25519-sha256@libssh.org"`  
`ssh_macs:       "hmac-sha2-512-etm@openssh.com"`  

The calculated variables are :  
`ansible_default_user_ssh_key: "{{ git_url }}{{ git_public_path }}{{ ansible_default_user }}@{{ inventory_hostname }}.pub"` where inventory_hostname is the name in your inventory (logic enough ?)  
