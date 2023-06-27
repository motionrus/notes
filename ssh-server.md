## Как настроить ssh-server на kubuntu-desktop
```
apt install openssh-server
chmod 700 ~/.ssh
ssh-keygen -t rsa

```

Меняем
```bash
# filePath: /etc/ssh/sshd_config
. . .
PasswordAuthentication no
. . .
```

Переименуем и перезапустим
```
cd ~/.ssh
mv id_rsa.pub authorized_keys
sudo service ssh restart
```

На клиент копируем приватный ключ `id_rsa` с правильными правами
```
-r--------@  1 rus  staff  2602 Jun 27 11:11 id_rsa
```

Настраиваем конфиг
```bash
# filePath: ~/.ssh/config 
Host softbox
    Hostname 1.2.3.4
    Port 1234
    User username
    IdentityFile ~/.ssh/id_rsa
```
