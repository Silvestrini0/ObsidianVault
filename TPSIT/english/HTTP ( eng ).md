# Evolution of HTTP

## HTTP/1.0

- **Non‑persistent model**: the client opens a new TCP connection for each request, which is closed after the response.
    
- **Problem**: downloading a page composed of many resources (e.g., images, CSS) requires opening numerous independent TCP connections, increasing latency and server load.
    

## HTTP/1.1

### Persistent Connections

- Allows sending multiple requests and receiving multiple responses over the same TCP connection.
    
- The connection is not closed immediately, reducing the number of TCP handshakes.
    

### Host Header

- Mandatory in HTTP/1.1.
    
- Enables **virtual hosting**: multiple domains can share the same IP address. The server reads the `Host` header to determine which website to serve.
    

### Pipelining

- The client can send several requests without waiting for the corresponding responses.
    
- **Problem**: the server is forced to respond in the same order the requests were received (sequential model).
    
- A slow response blocks all subsequent ones → **application‑level Head‑of‑Line blocking**.
    
- Pipelining was rarely used due to compatibility issues with intermediary proxies and the risk of blocking.
    

### Chunked Transfer Encoding

- The server can send the response in chunks without knowing the total length of the content in advance.
    
- Useful for dynamically generated content (e.g., pages that query a database or receive data from external services).
    
- Each chunk is preceded by its size; the client reconstructs the content as it arrives.
    

### Improved Caching

- HTTP/1.0 had basic mechanisms such as `Expires` and `If‑Modified‑Since`, based on timestamps.
    
- **HTTP/1.1** introduces:
    
    - `Cache‑Control`: defines precise caching policies (duration, visibility, validity).
        
    - `ETag` (Entity Tag): a unique identifier for a specific version of a resource.
        
    - The client can use `If‑None‑Match` with the ETag to ask the server whether the cached copy is still valid.
        
    - If the resource has not changed, the server replies with `304 Not Modified` (no body), reducing traffic.
        

## HTTP/2.0 (2015)

### Binary Architecture

- Messages are no longer ASCII text; they are split into **binary frames**.
    
- Each frame contains predefined fields: **Length**, **Type**, **Flags**, **Stream Identifier**, and **Payload**.
    
- The binary format simplifies parsing and reduces ambiguities.
    
- Headers are no longer sent as strings; they are encoded and compressed using **HPACK**.
    

### Multiplexing

- A single TCP connection carries multiple **independent logical streams**, each identified by a **Stream ID**.
    
- Frames from different streams are interleaved and sent over the same connection.
    
- The recipient uses the Stream ID to demultiplex the data and reconstruct the original streams.
    
- Eliminates application‑level Head‑of‑Line blocking (a slow response does not block others), but **TCP‑level blocking** remains (a lost packet stalls all streams).
    

### Other Features

- **Stream prioritisation**: the client can indicate the relative importance of each stream.
    
- **Server push** (optional): the server can send additional resources before the client explicitly requests them.
    

## HTTP/3.0 (2022)

### Overview

- Standardised in **RFC 9114**.
    
- Retains the stream model and frame architecture of HTTP/2, but replaces TCP with **QUIC** (based on UDP).
    

### Main Advantages

- **No transport‑level Head‑of‑Line blocking**: packet loss only affects the stream it belongs to; other streams continue unaffected.
    
- **Faster handshake**: often 0‑RTT (zero round‑trip time) for repeated connections thanks to QUIC.
    
- **Integrated encryption**: TLS 1.3 is part of QUIC, not a separate layer.
    
- **Connection migration**: the connection can survive IP address changes (e.g., from Wi‑Fi to cellular).
    

### Header Compression

- Uses **QPACK**, an adaptation of HPACK designed to work with QUIC’s multiplexing.
    

---

# QUIC (Quick UDP Internet Connections)

### Overview

- **QUIC** is a transport protocol developed by Google, standardised in **RFC 9000**.
    
- It operates over **UDP** but internally implements reliability, congestion control, and multiplexing, overcoming some limitations of TCP.
    

### Reliability and Congestion Control

- **Unique packet numbers**: enable loss detection, duplicate identification, and correct ordering.
    
- **Ack frames**: acknowledgements are carried as frames inside QUIC packet payloads; the sender retransmits if no Ack is received.
    
- **Congestion control**: internal algorithms (similar to TCP ones) dynamically adjust the sending rate based on network conditions.
    

### Multiplexing and Independent Stream Management

- Data is split into **frames**, each associated with an **independent stream** (identified by a stream ID).
    
- Each stream maintains its own data sequence, flow control, reliability, and retransmissions.
    
- Frames from different streams are interleaved within the same QUIC packets, enabling parallel, non‑blocking communication.
    
- When a packet is lost, only the data of the affected streams is retransmitted, without impacting others.
    

### Security

- QUIC integrates **TLS 1.3** directly, providing end‑to‑end encryption and authentication from the very start of the connection.
    

### Encapsulation

- Frames are placed into QUIC packets, which travel over UDP. Within the same QUIC packet, frames from different streams can coexist.