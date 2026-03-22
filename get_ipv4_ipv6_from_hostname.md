To get the IPv4 and IPv6 addresses of a public domain name on RHEL, use the following methods:

1. `getent`

>This method queries the system's Name Service Switch (NSS) configuration:

```
[hungtx@localhost ~]$ getent ahosts google.com
2a00:1450:4001:828::200e STREAM google.com
2a00:1450:4001:828::200e DGRAM  
2a00:1450:4001:828::200e RAW    
142.250.185.174 STREAM 
142.250.185.174 DGRAM  
142.250.185.174 RAW    
[hungtx@localhost ~]$ getent ahosts google.com | awk '/STREAM/ {print $1}'
2a00:1450:4001:828::200e
142.250.185.174
[hungtx@localhost ~]$ getent ahosts google.com | awk '{print $1}' 
2a00:1450:4001:828::200e
2a00:1450:4001:828::200e
2a00:1450:4001:828::200e
142.250.186.78
142.250.186.78
142.250.186.78

```

2. `dig`

```
[hungtx@linux ~]$ dig A youtube.com +short
142.250.185.174
[hungtx@linux ~]$ dig AAAA youtube.com +short
2a00:1450:4001:800::200e
[hungtx@linux ~]$ 
```

3. `host`

```
[hungtx@linux ~]$ host -t A youtube.com
youtube.com has address 172.217.23.110
[hungtx@linux ~]$ host -t AAAA youtube.com
youtube.com has IPv6 address 2a00:1450:4001:800::200e
[hungtx@linux ~]$ host -a youtube.com
Trying "youtube.com"
Trying "youtube.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22991
;; flags: qr rd ra; QUERY: 1, ANSWER: 8, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;youtube.com.			IN	ANY

;; ANSWER SECTION:
youtube.com.		5388	IN	NS	ns2.google.com.
youtube.com.		5388	IN	NS	ns1.google.com.
youtube.com.		14	IN	AAAA	2a00:1450:4001:800::200e
youtube.com.		58	IN	A	172.217.23.110
youtube.com.		5388	IN	NS	ns4.google.com.
youtube.com.		69	IN	HTTPS	1 .
youtube.com.		5388	IN	NS	ns3.google.com.
youtube.com.		180	IN	MX	0 smtp.google.com.

Received 188 bytes from 192.168.178.1#53 in 3 ms
[hungtx@linux ~]$ host -A youtube.com
Trying "youtube.com"
Trying "youtube.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37059
;; flags: qr rd ra; QUERY: 1, ANSWER: 8, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;youtube.com.			IN	ANY

;; ANSWER SECTION:
youtube.com.		5385	IN	NS	ns2.google.com.
youtube.com.		5385	IN	NS	ns1.google.com.
youtube.com.		11	IN	AAAA	2a00:1450:4001:800::200e
youtube.com.		55	IN	A	172.217.23.110
youtube.com.		5385	IN	NS	ns4.google.com.
youtube.com.		66	IN	HTTPS	1 .
youtube.com.		5385	IN	NS	ns3.google.com.
youtube.com.		177	IN	MX	0 smtp.google.com.

Received 188 bytes from 192.168.178.1#53 in 5 ms
[hungtx@linux ~]$ 
```

4. `nslookup`

```
hungtx@linux ~]$ nslookup youtube.com
Server:		192.168.178.1
Address:	192.168.178.1#53

Non-authoritative answer:
Name:	youtube.com
Address: 172.217.23.110
Name:	youtube.com
Address: 2a00:1450:4001:811::200e

[hungtx@linux ~]$ nslookup -query=A youtube.com
Server:		192.168.178.1
Address:	192.168.178.1#53

Non-authoritative answer:
Name:	youtube.com
Address: 172.217.23.110

[hungtx@linux ~]$ nslookup -query=AAAA youtube.com
Server:		192.168.178.1
Address:	192.168.178.1#53

Non-authoritative answer:
Name:	youtube.com
Address: 2a00:1450:4001:811::200e

[hungtx@linux ~]$ 

```

5. Using `ping -4`, `ping -6` or `ping6`

