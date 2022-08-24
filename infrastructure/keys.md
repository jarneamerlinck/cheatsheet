# Keys and certificates

## ssh keys
## ssl certificates
| What                            | Command                                                                                                                 |
| ------------------------------- | :---------------------------------------------------------------------------------------------------------------------- |
| create self signed certificates | ```sudo openssl req -days 365 -newkey rsa:2048 -x509 -nodes -out /etc/ssl/certs/vsftpd.crt -keyout /etc/ssl/private/``` |

## gpg keys

| What                            | Command     |
| ------------------------------- | :---------- |
| create gpg key | ```gpg --gen-key``` |



### gpg key gen options
1. Kind of key
   1. RSA and RSA (default)
      > This is the default value
   2. DSA and Elgamal
      > This is the default value
   3. DSA (sign only)
      > This is the default value
   4. RSA (sign only)
      > This is the default value

