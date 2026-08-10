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
- PING

### UPD
- UDP [[Wiki](https://en.wikipedia.org/wiki/User_Datagram_Protocol)] [[CF]
- TCP Meltdown [[Article](https://openvpn.net/as-docs/faq-tcp-meltdown.html)]
- DNS Poisoning [[CF](https://www.cloudflare.com/learning/dns/dns-cache-poisoning/)]
- DNS Flooding [[CF](https://www.cloudflare.com/learning/ddos/dns-flood-ddos-attack/)]
- `nc` Tool [[Article](https://www.kali.org/tools/netcat/)]

### TCP
- TCP [[Wiki](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)] [[CF](https://developers.cloudflare.com/fundamentals/reference/tcp-connections/)]
- Ports [[Wiki](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)]
- HTTP [[Wiki](https://en.wikipedia.org/wiki/HTTP)]
- File Descriptors [[Wiki](https://en.wikipedia.org/wiki/File_descriptor)] [[Article](https://www.linkedin.com/pulse/linux-sockets-file-descriptors-understanding-leaks-breaking-dhyani-mfwkc/)]
- SYN Flood Attack [[CF](https://www.cloudflare.com/learning/ddos/syn-flood-ddos-attack/)]
- TCP Handshake [[MDN](https://www.cloudflare.com/learning/ddos/syn-flood-ddos-attack/)]
- TCP Sequences [See Wiki Again]
- Multipath TCP [[Wiki](https://en.wikipedia.org/wiki/Multipath_TCP)]
- Millions of TCP Connections [[Whatsapp Blog](https://blog.whatsapp.com/1-million-is-so-2011)]

## TLS
- Layer 5? Session layer
- TLS Handshake
- HTTPS
- Symmetric Key Algorithms For Encryption
- Asymeetric ones for key exchange
- PKI (Public Key Infrastructure)
- RSA For Forward Secrecy
- Epehmeral Keys (Diffie Helman)
- TLS 1.2 (2 roundtrips) vs 1.3 (one / zero roundtrips)
- Key size
- key generation
- digital signature algos
- client side certs

## HTTP
- HTTP 1.0 / 1.1 / 2 / 3
- HTTP client & server
- Hosting multiple domains on same IP - host header differentiates - Multi Homed Websites
- HTTP vs HTTPS
- Transfer Encoding - Chunked
- HTTP Smuggling
- Pipelining in HTTP 1.1
- Protocol Ossification
- SPDY in HTTP2
- NPN / ALPN
- HTTP 3 / HTTP over QUIC

## HTTPS, TLS, Keys, & Certificates
- SNI (Server Name Indication)
- ECH (Encrypted Client Hello)
- Encrypting With Private Key And Public Key
- Certificates, x509, ROOT certificate, chains
- Heartbleed Attack
- openssl

## Web-Sockets
- ws handshake
- Need for HTTP/1.1 for websockets
- ws:// or wss://
- upgrade header
- why proxying with WS is hard
- ping pong in websockets
- server sent events vs ws

## HTTP/2
- multiplexing over single connections
- header and data compression
- protocol negotiation during tcp
- tcp head of line blocking
- high cpu usage

## HTTP/3
- QUIC
- congestion control at http3
- connection migration using connection id
- why not http2 over quic - header compression algo risk. Check out CRIME security vulnerability
- CPU usage in QUIC
- IP Fragmentation in Http3

## gRPC
- Unary RPC, server streaming rpc, client streaming rpc, bidirectional streaming rpc
- cancellable requests (HTTP/2)
- proxies are difficult in grpc
- spotify protocol
