## Given:
| Interface | IP Address     | Subnet Mask       | Prefix | 
|-----------|----------------|-------------------|--------|
| A1        |                | 255.255.255.224   | /27    |
| B1        | 192.168.65.222 |                   |        | 
| C1        |                | 255.255.255.252   |        |
| D1        |                |                   | /30    |

## Solution 1: A1 & B1

- Determine the subnet range for Interface B1 using the subnet mask `255.255.255.224` (/27). This mask allows for 32 IP addresses per subnet, with 30 usable IPs after excluding the network and broadcast addresses.

- Choose an IP address for Interface A1 that is within the same subnet as Interface B1. For example, if Interface B1 has an IP address of `192.168.1.2`, then Interface A1 could be assigned `192.168.1.3` as both would fall within the `192.168.1.0/27` subnet range.

3. Ensure both interfaces are configured to use the same subnet mask of `255.255.255.224`.

## Solution 2: C1 & D1

- Both subnet masks indicate a very small network with only 4 addresses in total, of which 2 are usable for devices. This is because the subnet mask `255.255.255.252` or `/30` leaves only 2 bits for host addresses.
- For C1 and D1 to communicate, they must be in the same subnet. 
- **C1 IP Address**: `192.168.1.2` - This is the first usable IP in the subnet.
- **D1 IP Address**: `192.168.1.1` - This is the second and last usable IP in the subnet.


![level02](level02/level2.png "This is level 02 config")