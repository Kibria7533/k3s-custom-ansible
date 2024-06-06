# To start the ansible playbook please give the root user or any user permission to create the cluster

For my case i am giving the root user the permission

# Steps to Enable Root User Access Without Password Using SSH Key

## 1. Generate SSH Key Pair (if not already done)

On your local machine, generate an SSH key pair if you don't have one already:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"


This command will generate a public and private key pair. The public key will be named id_rsa.pub and the private key id_rsa by default. 
```

# 2. Copy the Public Key to the Server
```bash
ssh-copy-id root@your_server_ip
```

# 3. Configure SSH Daemon on the Server
Edit the SSH daemon configuration file to allow root login with SSH keys:
```bash
nano /etc/ssh/sshd_config
```
And make root login 
```
PermitRootLogin yes
```
# 4. Restart SSH Service
```bash
systemctl restart sshd
```

# 5. Test SSH Login
```bash
ssh root@your_server_ip
```

# Ans finanlly to run the ansible playbook command
```bash
ansible-playbook -i inventory.ini playbook.yml  -vvvv
```