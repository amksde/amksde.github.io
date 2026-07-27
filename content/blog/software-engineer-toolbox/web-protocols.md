---
title: "Networking & Web Protocols"
---

Follow a request from the browser or client to a service and back.

- DNS resolution, IP addressing, TCP handshakes/flow control, TLS handshakes/certificates, and HTTP requests.
- HTTP methods, safety/idempotency, status codes, headers, content negotiation, redirects, caching, compression, byte ranges, and conditional requests.
- HTTP/1.1 connection reuse, HTTP/2 multiplexing, HTTP/3/QUIC, timeouts, proxies, load balancers, and connection pools.
- Cookies, sessions, CORS, CSRF, CSP, same-site policy, bearer tokens, and browser security boundaries.
- REST, GraphQL, gRPC, WebSockets, Server-Sent Events, webhooks, and SMTP/email delivery basics.
- Use `curl`, browser developer tools, `dig`, `nslookup`, `openssl s_client`, `tcpdump`, and service logs to debug real failures.


## Networking
- OSI Model [[Cloudflare](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)] [[Wiki](https://en.wikipedia.org/wiki/OSI_model)]

### Internet Protocol
- Internet Protocol [[Cloudflare](https://www.cloudflare.com/learning/network-layer/internet-protocol/)] [[Wiki](https://en.wikipedia.org/wiki/Internet_Protocol)]
- Subnet [[Cloudflare](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/)]
- MTU [[Cloudflare](https://www.cloudflare.com/learning/network-layer/what-is-mtu/)]
- Packet [[CF](https://www.cloudflare.com/learning/network-layer/what-is-a-packet/)] [[Wiki](https://en.wikipedia.org/wiki/IP_packet)]
- IP Fragmentation [[Wiki](https://en.wikipedia.org/wiki/IP_fragmentation)]
- ICMP [[CF](https://www.cloudflare.com/learning/ddos/glossary/internet-control-message-protocol-icmp/)]
- IP Protocols [[Wiki](https://en.wikipedia.org/wiki/List_of_IP_protocol_numbers)]
- ECN [[Wiki](https://en.wikipedia.org/wiki/Explicit_Congestion_Notification)]
- TCP Blackhole [[Wiki](https://en.wikipedia.org/wiki/Black_hole_(networking))]
- Traceroute [[Wiki](https://en.wikipedia.org/wiki/Traceroute)]
