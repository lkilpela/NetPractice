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
- Interface B1 need to communicate with Interface R2. 
    - R2 has a subnet mask of `255.255.192.0` (or `/18` prefix), B1 and R2 must be in the same subnet.
    - Router's Interface R2 has IP address `166.155.236.254`
    - Usable IP range: `166.155.192.1 - 166.155.255.254`.

- Interface A1 need to communicate with Interface R1. 
    - R2 has a subnet mask of `255.255.255.128` (or `/25` prefix), B1 and R2 must be in the same subnet.
    - Router's Interface R2 has IP address `97.175.35.126`
    - Usable IP range: `97.175.35.1 - 97.175.35.125`.


#### Calculation:
Subnet mask: 255.255.192.0. Focus on the octet where subnetting occurs, which is the third octet in this case (192).

- Block size: `256 - 192 = 0`.
blocks in the third octet start at multiples of 64 (0, 64, 128, 192, etc.).
- To find the starting point of the block for a given IP address, divide the third octet by the block size (64) and then multiply back by 64 to get the lower boundary.
- For an IP address `166.155.236.254`, the third octet is `236`.
- Calculate the starting block: 
`(236 / 64) = 3.6875.` 

Since we're interested in the starting point, we take the integer part (3) and multiply by the block size (64): `3 * 64 = 192.`
- Use the first two octets from the original IP address (166.155), the calculated starting point for the third octet (192), and set the fourth octet to 0 (since we're calculating the network address).
This gives us the network address: 166.155.192.0. 
Usable IP range: `166.155.192.1 - 166.155.255.254`.








| Interface | IP Address      | Subnet Mask     | Prefix | Destination | Next Hop        |
|-----------|-----------------|-----------------|--------|-------------|-----------------|
| R1        | 97.175.35.126   | 255.255.255.128 |        |             |                 |
| R2        | 166.155.236.254 | 255.255.192.0   |        |             |                 |
| A1        |                 |                 |        |  default    | 97.175.35.126   |   
| B1        |                 |                 |        |  default    | 166.155.236.254 |