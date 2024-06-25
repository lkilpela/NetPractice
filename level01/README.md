## Given:
Interface B1:
- IP address: 104.99.23.12
- Subnet mask: 255.255.255.0

Interface C1:
- IP address: 211.191.20.75
- Subnet mask: 255.255.255.0

## Subnet Details:
- The subnet mask 255.255.255.0 corresponds to a /24 prefix.
- This means the network address is determined by the first 24 bits of the IP address.

## Solution:

1. To communicate with Interface B1, Interface A1 must be in the same subnet `(104.99.23.0/24)`.
- The subnet mask for Interface A1 should also be `255.255.255.0`.
- The IP address for Interface A1 should be any address in the range `104.99.23.1` to `104.99.23.254`, except 104.99.23.12 (since that is used by Interface B1), 104.99.23.0 (Network address) and 104.99.23.255 (Broadcast address).

2. To communicate with Interface C1, Interface D1 must be in the same subnet `(211.191.20.0/24)`.
- The subnet mask for Interface D1 should also be `255.255.255.0`.
- The IP address for Interface D1 should be any address in the range 211.191.20.1 to 211.191.20.254, except 211.191.20.75 (since that is used by Interface C1), 211.191.203.0 (Network address) and 211.191.20.255 (Broadcast address).

![level01](level01/level01.png "This is level 01 config")
