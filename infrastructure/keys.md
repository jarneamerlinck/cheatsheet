# Keys and certificates

## ssh keys
## ssl certificates
| What                            | Command                                                                                                                 |
| ------------------------------- | :---------------------------------------------------------------------------------------------------------------------- |
| create self signed certificates | ```sudo openssl req -days 365 -newkey rsa:2048 -x509 -nodes -out /etc/ssl/certs/vsftpd.crt -keyout /etc/ssl/private/``` |

## gpg keys






## gpg keys

| What                                              | Command                                                                   |
| ------------------------------------------------- | :------------------------------------------------------------------------ |
| create gpg key                                    | ```gpg --full-generate-key```                                             |
| list public keys                                  | ```gpg --list-keys```                                                     |
| list secret keys                                  | ```gpg --list-secret-keys```                                              |
| export public key                                 | ```gpg -a --export KEYID > public.asc```                                  |
| export secret key                                 | ```gpg -a --export-secret-key KEYID > secret.asc```                       |
| list exported key                                 | ```gpg public.asc```                                                      |
| list fingerprint exported key                     | ```gpg --with-subkey-fingerprint public.asc```                            |
| import exported key                               | ```gpg --import keys.asc```                                               |
| see finger print                                  | ```gpg --fingerprint KEYID```                                             |
| sign key                                          | ```gpg --sign-key KEYID```                                                |
| local sign key                                    | ```gpg --lsign-key KEYID```                                               |
| remove signature from key (use lsign to find UID) | ```gpg --edit-key KEYID``` <br> ```gpg>delsig UID```  <br> ```gpg>save``` |
| encrypt file                                      | ```gpg --default-key KEYID -a -s file.txt```                              |
| verify encryption                                 | ```gpg --verify file.txt.asc```                                           |
| List recipients of a encrypted file               | ```gpg --list-only FILE```                                                |
| decrypt file                                      | ```gpg -d -o OUTPUT FILE```                                               |


