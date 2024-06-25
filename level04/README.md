## This level introduces the router.

A router is a device that forwards data packets between different networks, typically between a local network and the internet. It uses IP addresses to determine the best path for forwarding the packets.

## Info Given:
| Interface | IP Address      | Subnet Mask     | Prefix | 
|-----------|-----------------|-----------------|--------|
| R1        |                 |                 |        |
| R2        | 123.247.112.1   | 255.255.255.128 |        | 
| R3        | 123.247.112.244 | 255.255.255.192 |        |
| A1        | 123.247.112.132 |                 |        |
| B1        |                 |                 |        |

## Solution

### Step 1: Choosing a Subnet Mask:
- Assigning a /24 subnet mask (255.255.255.0) to interfaces A1, B1, and R1 simplifies the subnetting process. This mask divides the IP address space into networks where the first three octets are the network address, and the fourth octet is used for host addresses within that network.

### Step 2: Determining IP Address Range:
- With a /24 subnet mask, the usable IP address range for the network is `123.247.112.1 to 123.247.112.254`. Except the network address `(123.247.112.0)` and the broadcast address `(123.247.112.255)`.

### Step 3: Assigning IP Addresses:
- Interface A1 already has an IP address within this range. Interfaces B1 and R1 can be assigned any other IP addresses within this range, ensuring they are not the network or broadcast addresses and do not conflict with A1's address.

| Interface | IP Address      | Subnet Mask     | Prefix | 
|-----------|-----------------|-----------------|--------|
| R1        | 123.247.112.134 |                 | /24    |
| R2        | 123.247.112.1   | 255.255.255.128 | /25    | 
| R3        | 123.247.112.244 | 255.255.255.192 | /26    |
| A1        | 123.247.112.132 |                 | /24    |
| B1        | 123.247.112.133 |                 | /24    |

