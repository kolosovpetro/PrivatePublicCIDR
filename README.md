# IPv4 Public and Private Address Ranges

## Purpose

This document explains how IPv4 addresses are categorized into public and private ranges. It describes the reserved private address spaces, other special-purpose ranges, and provides guidance on distinguishing internal addresses from publicly routable ones.

## Basic rule for identifying private addresses

| IP Range | Private |
|----------|---------|
| 10.x.x.x | Yes |
| 172.16.x.x – 172.31.x.x | Yes |
| 192.168.x.x | Yes |

## Private ranges defined in RFC 1918

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

## Public IPv4 Addresses

Public IPv4 addresses are globally routable on the Internet. Any address that does not belong to a reserved or special-purpose range can be assigned to a device that is reachable from the Internet.

### Examples of public IP addresses

- 8.8.8.8
- 104.18.1.163
- 52.167.144.12
- 172.220.38.63

Public IP addresses are allocated by regional Internet registries and are used by servers, cloud infrastructure, websites, and public services.

## Private IPv4 Address Space

Private address ranges are reserved for use within internal networks and are not routable on the public Internet. These ranges were defined in RFC 1918.

### Private ranges

- 10.0.0.0/8
  - Range
  - 10.0.0.0 – 10.255.255.255
  - Total addresses
  - 16777216

- 172.16.0.0/12
  - Range
  - 172.16.0.0 – 172.31.255.255
  - Total addresses
  - 1048576

- 192.168.0.0/16
  - Range
  - 192.168.0.0 – 192.168.255.255
  - Total addresses
  - 65536

### Typical uses

- 10.0.0.0/8
  - Large enterprise networks
  - Cloud virtual networks

- 172.16.0.0/12
  - Corporate infrastructure
  - Medium internal networks

- 192.168.0.0/16
  - Home networks
  - Small office routers

Devices in private networks typically access the Internet through Network Address Translation.

## Network Address Translation

Network Address Translation allows multiple devices using private addresses to share a single public IP address when accessing the Internet.

### Example flow

1. Internal device
   - 192.168.1.25

2. Router performs NAT

3. Public address
   - 203.0.113.5

The router maps the internal address and port to a public address and port.

## Special Purpose IPv4 Ranges

Several additional IPv4 ranges are reserved for special networking purposes.

### Loopback range

- 127.0.0.0/8
  - Purpose
    - Localhost communication within the same machine
  - Example
    - 127.0.0.1

### Link local range

- 169.254.0.0/16
  - Purpose
    - Automatic address assignment when DHCP is unavailable

### Carrier grade NAT

- 100.64.0.0/10
  - Purpose
    - Used by Internet service providers to share public IPv4 addresses between customers

### Multicast

- 224.0.0.0/4
  - Purpose
    - Multicast communication such as streaming or routing protocols

### Reserved future use

- 240.0.0.0/4
  - Purpose
    - Reserved for future use

## Distinguishing Public and Private Addresses

### Basic rule for identifying private addresses

- 10.x.x.x is private
- 172.16.x.x through 172.31.x.x is private
- 192.168.x.x is private

If an address does not fall within these ranges, it is usually public.

### Examples

- 10.5.4.3
  - Private

- 172.20.10.5
  - Private

- 192.168.1.10
  - Private

- 104.18.1.163
  - Public

- 8.8.8.8
  - Public

- 172.220.38.63
  - Public range but may be used internally in some environments

## Use of Non RFC1918 Ranges in Internal Systems

Some systems intentionally use address ranges that are technically public but confined within a private routing domain.

Examples include container orchestration systems and overlay networks.

### Examples

- Kubernetes service networks
  - 172.220.0.0/16

- Container overlay networks
  - 100.96.0.0/11

These addresses are internal because routing rules prevent them from leaving the environment.

## Practical Examples in Cloud Environments

### Typical address categories in cloud systems

- Public Internet IP
  - 52.160.14.10

- Cloud virtual network address
  - 10.1.0.5

- Kubernetes pod address
  - 10.244.2.18

- Kubernetes service address
  - 172.220.38.63

- Internal load balancer address
  - 10.110.56.200

- External CDN address
  - 104.18.0.163

## Summary

IPv4 addresses fall into two major categories: public and private.

### Private ranges defined in RFC 1918

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

All other IPv4 addresses are generally public unless reserved for special purposes.

Understanding these ranges is essential for network debugging, cloud infrastructure design, and troubleshooting connectivity issues.