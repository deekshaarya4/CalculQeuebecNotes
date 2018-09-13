### Connect to Server using ssh:
Ref: https://wiki.calculquebec.ca/w/Connexion_%C3%A0_l%27aide_des_cl%C3%A9s_publiques_et_priv%C3%A9es/en
1. `[local]> ssh-keygen -t rsa -f ~/.ssh/calcul_quebec` (enter a passphrase - required for calcul quebec servers)
2. `[cq_server]> mkdir -p ~/.ssh`
3. `[local]> scp ~/.ssh/calcul_quebec.pub username@server.calcul_quebec.ca:.ssh/username_local.pub`
4. `[cq_server]> cd ~/.ssh; cat username_local.pub >> authorized_keys`
5. On local, open `~/.ssh/config` and add:
  ```
  Host cq_server_shortform #(eg. guillimin)
            HostName cq_server #(eg. guillimin.hpc.mcgill.ca)
            User cq_server_username
            Port 22
            IdentityFile /Users/local_username/.ssh/calcul_quebec
  ```
6. `[local]> ssh-add ~/.ssh/calcul_quebec` (Enter passphrase)
7. `[local]> ssh cq_server_username@cq_server` OR simply `[local]> ssh cq_server_shortform`

### Copy data to server:
`[local]> scp -r data cq_server_username@cq_server:`
