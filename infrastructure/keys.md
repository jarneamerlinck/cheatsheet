# Keys and certificates

## ssh keys
## ssl certificates

### Certificate Authority (CA)

- All trusted CA's are stored on each machine
  - Linux:  ```/etc/pki/ca-trust/extracted```
  - Windows run ```msc``` and look for ```Trusted Root Certification Authorities -> Certificates```


| What                      | Command                                                                    |
| ------------------------- | :------------------------------------------------------------------------- |
| Generate CA               | ```openssl genrsa -aes256 -out ca-key.pem 4096```                          |
| Generate a public CA Cert | ```openssl req -new -x509 -sha256 -days 365 -key ca-key.pem -out ca.pem``` |
| See cert in text format   | ```openssl x509 -in ca.pem -text```                                        |



### Certificates

| What                    | Command                                                                                                                                |
| ----------------------- | :------------------------------------------------------------------------------------------------------------------------------------- |
| Generate cert key       | ```openssl genrsa -out cert-key.pem 4096```                                                                                            |
| Generate sign request   | ```openssl req -new -sha256 -subj "/CN=yourcn" -key cert-key.pem -out cert.csr```                                                      |
| Generate dns to ip link | ```echo "subjectAltName=DNS:your-dns.record,IP:257.10.10.1" >> extfile.cnf```                                                          |
| Generate cert           | ```openssl x509 -req -sha256 -days 365 -in cert.csr -CA ca.pem -CAkey ca-key.pem -out cert.pem -extfile extfile.cnf -CAcreateserial``` |
| Check  certs            | ```openssl verify -CAfile ca.pem -verbose cert.pem```                                                                                  |
| Combine certs           | ```cat cert.pem > fullchain.pem;cat ca.pem>>fullchain.pem```                                                                           |



### Import CA in client
| Where                                                                                       | Command                                                                                                        |
| ------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------- |
| [Debian](https://wiki.debian.org/Self-Signed_Certificate)                                   | Move ca.pem to ```/usr/local/share/ca-certificates/ca.crt``` <br> ```sudo update-ca-certificates```            |
| [Fedora](https://docs.fedoraproject.org/en-US/quick-docs/using-shared-system-certificates/) | Move ca.pem to ```/etc/pki/ca-trust/source/anchors/ca.pem``` <br> ```sudo update-ca-trust```                   |
| [Arch](https://wiki.archlinux.org/title/User:Grawity/Adding_a_trusted_CA_certificate)       | ```trust anchor --store ca.pem``` <br> ```update-ca-trust```                                                   |
| Android                                                                                     | Find ```Encryption and Credential```   under ```Settings > Security > Encryption and Credentials```            |
| Windows                                                                                     | run as administrator ```Import-Certificate -FilePath "C:\ca.pem" -CertStoreLocation Cert:\LocalMachine\Root``` |


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


