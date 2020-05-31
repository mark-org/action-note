# ssh下known_hosts的作用

ssh会把你每个你访问过计算机的公钥(public key)都记录在~/.ssh/known_hosts。当下次访问相同计算机时，
OpenSSH会核对公钥。如果公钥不同，OpenSSH会发出警告， 避免你受到DNS Hijack之类的攻击。我在上面列出的情况，就是这种情况。

# id_rsa.pub 公钥其实就是id_rsa.pub。

# 私钥 id_rsa ssh命令默认只会读取 id_rsa这个私钥

# SSH 2 公钥格式
选项、密钥类型（keytype）、base64编码后的密钥、注释默认注释为密钥的创建者（一般就是 username@hostname 这种格式）
第一个字段是可选的，表示该条目（行）是否以数字开头
密钥类型（keytype）:ssh-rsa