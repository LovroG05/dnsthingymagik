# DNSThingyMagiK

This is my simple, barebones, **insecure** implementation of a simple DNS server meant for local use. The goal is to support RFC 1035, local records, ad blocking.

For now, it successfully recursively resolves A records.

Sends through correct TTL values.

## Testing

`dig @serverip domain.tld`

Example:

```shell
lovro@LHPw:~$ dig @193.2.231.164 govekar.net

; <<>> DiG 9.18.30-0ubuntu0.24.04.2-Ubuntu <<>> @193.2.231.164 govekar.net
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6752
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;govekar.net.                   IN      A

;; ANSWER SECTION:
govekar.net.            300     IN      A       185.199.109.153
govekar.net.            300     IN      A       185.199.111.153
govekar.net.            300     IN      A       185.199.110.153
govekar.net.            300     IN      A       185.199.108.153

;; Query time: 167 msec
;; SERVER: 193.2.231.164#53(193.2.231.164) (UDP)
;; WHEN: Tue Mar 11 17:40:16 CET 2025
;; MSG SIZE  rcvd: 93

lovro@LHPw:~$
```

with 8.8.8.8:

```shell
lovro@LHPw:~$ dig @8.8.8.8 govekar.net

; <<>> DiG 9.18.30-0ubuntu0.24.04.2-Ubuntu <<>> @8.8.8.8 govekar.net
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19053
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;govekar.net.                   IN      A

;; ANSWER SECTION:
govekar.net.            300     IN      A       185.199.110.153
govekar.net.            300     IN      A       185.199.109.153
govekar.net.            300     IN      A       185.199.111.153
govekar.net.            300     IN      A       185.199.108.153

;; Query time: 51 msec
;; SERVER: 8.8.8.8#53(8.8.8.8) (UDP)
;; WHEN: Tue Mar 11 16:22:12 CET 2025
;; MSG SIZE  rcvd: 104

lovro@LHPw:~$
```
