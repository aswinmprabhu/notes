DNS resolution on linux  
  
**getaddrinfo** -> **/etc/services** to resolve port for a service (ex: http is 80) -> Query **nscd (name servce cache daemon)** for local cache -> **/etc/nsswitch.conf (Name service switch)** determines order of resolution -> **/etc/hosts** (for the files option) -> **/etc/resolv.conf** (Addr of the DNS server) -> Query DNS

---
