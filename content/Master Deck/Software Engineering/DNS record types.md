DNS record types

---
A (Address record)  
Maps hostnames to 32bit IPv4 address  
example.com -> 192.0.2.1  
@ indicates root domain  
Default ttl 4hrs  
  
AAAA (IPv6 address record)  
Maps hostnames to 128bit IPv6 address  
  
CNAME (Canonical name record)  
Alias of one name to another  
blog.example.com -> example.com  
  
NS (Name server record)  
Delegates a [DNS zone](https://en.wikipedia.org/wiki/DNS_zone) to use the given [authoritative name servers](https://en.wikipedia.org/wiki/Authoritative_name_server)  
  
MX (Mail exchange record)  
List of mail exchange servers that accept email for a domain  
example.com -> mailhost1.example.com  
Has prio (lower is greater)  
  
DNAME (Delegation name record)  
Creates an alias for an entire subtree of the domain name tree  
  
TXT (Text record)  
Arbitrary text in DNS record  
  
SOA (Start of authority record)  
Stores admin info  
  
SRV (Service record)  
Specifies host and port for specific services (voip)  
  
PTR (Pointer record)  
Reverse of A record used for reverse DNS lookups (useful for email spam filters and logging)  
192.0.2.255 becomes 255.2.0.192.in-addr.arpa -> example.com