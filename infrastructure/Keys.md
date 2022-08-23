# Keys and certificates

## ssh keys
## ssl certificates
| What                    | Command                                                                                                                 |
| ----------------------- | :---------------------------------------------------------------------------------------------------------------------- |
| create self signed certificates | ```sudo openssl req -days 365 -newkey rsa:2048 -x509 -nodes -out /etc/ssl/certs/vsftpd.crt -keyout /etc/ssl/private/``` |

## gpg keys