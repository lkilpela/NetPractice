## This level introduces the ROUTE.

In networking, a route generally consists of two main parts:

- Destination Network: This is the network that you're trying to reach. It's usually specified as an IP address and a subnet mask (or CIDR notation), which together define the range of IP addresses in the destination network.

- Next Hop: This is the next point (usually a router) that packets should be sent to on the way to the destination network. It's specified as an IP address.

## Info Given:
| Interface | IP Address      | Subnet Mask     | Prefix | Destination | Next Hop |
|-----------|-----------------|-----------------|--------|-------------|----------|
| R1        | 97.175.35.126   | 255.255.255.128 |        |             |          |
| R2        | 166.155.236.254 | 255.255.192.0   |        |             |          |
| A1        |                 |                 |        |             |          |   
| B1        |                 |                 |        |             |          |

## Solution

### Step 1: Understanding the Destination Network
- The **destination network** is where the outbound packets are intended to go. By default, a destination of `0.0.0.0/0` (also known as the default route) is used to send packets to any network not explicitly defined in the routing table.
- A specific destination, like `122.3.5.3/24`, targets packets to the `122.3.5.0` network, directing them to a particular subnet.

### Step 2: Determining the Next Hop
- The **next hop** is the immediate next destination to which packets are sent on their way to the final destination. It's crucial for routing packets beyond the local network.
- For a client with only one route out (like Client A in our scenario), the default destination (`0.0.0.0/0`) is used, as it allows sending packets to any network via the available path.

### Step 3: Configuring the Route for Client A & B
- Since Client A & B has only one path for sending packets, we don't need to specify a numbered destination. The packets will follow the default route.
- The next hop for Client A's packets is determined by the next router interface they encounter. In this case, the next hop IP address is `97.175.35.126`, which belongs to Interface R1. This is the interface on the next router that Client A must send its packets to, not Interface A1, as A1 represents the sender's own interface.
- Same for Client B's packets, the next hop IP address is `166.155.236.254`.

### Step 4: Configuring the subnet mask and IP address for Interface A1 & B1
- Since all devices must communicate with each other and Interface R2 has a subnet mask of `255.255.192.0` (or `/18` prefix), A1 and B1 must be in the same subnet.
- Router's Interface R2 has IP address `166.155.236.254`





| Interface | IP Address      | Subnet Mask     | Prefix | Destination | Next Hop        |
|-----------|-----------------|-----------------|--------|-------------|-----------------|
| R1        | 97.175.35.126   | 255.255.255.128 |        |             |                 |
| R2        | 166.155.236.254 | 255.255.192.0   |        |             |                 |
| A1        |                 |                 |        |  default    | 97.175.35.126   |   
| B1        |                 |                 |        |  default    | 166.155.236.254 |