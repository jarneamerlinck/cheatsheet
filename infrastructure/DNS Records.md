---
topic: DNS records
date: 2023/04/21
project: cheatsheet
type: note
---

# DNS Records
[Readme](../README.md)

> DNS (aka zone files) are instructions that live in authoritative DNS servers and provide information about a domain including what IP-address is associated with that domain and how to handle requests for that domain.

## Type of Records
## A

> A record is the record that holds the IP address of a domain.
### AAAA record

> AAAA record is the record that contains the IPv6 address for a domain (as opposed to A records, which list the IPv4 address).
### CNAME record

> Forwards one domain or subdomain to another domain, does NOT provide an IP address.

### MX record

> Directs mail to an email server.
### TXT record

> Lets an admin store text notes in the record. These records are often used for email security.
### Reverse PTR record

>  PTR record or more appropriately a reverse PTR record is a process of resolving an IP address to its associated hostname. This is the exact opposite of the process of resolving a hostname to an IP address (`A` record)
### SPF record

> SPF (TXT record) is a spam and phishing scam fighting method which uses DNS SPF-records to define which hosts are permitted to send e-mails for a domain.
### DKIM record

> DKIM (TXT record) defines a domain-level digital signature authentication framework for email through the use of public-key cryptography and using the domain name service as its key server technology.
### DMARC record

> DMARC (TXT record) is a way to make it easier for email senders and receivers to determine whether or not a given message is legitimately from the sender, and what to do if it isn’t. This makes it easier to identify spam and phishing messages, and keep them out of peoples’ inboxes.

