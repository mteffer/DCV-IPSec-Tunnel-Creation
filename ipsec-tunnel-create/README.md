# DCV-IPSec-Tunnel-Creation 
This skillet will take input variables and configure an IPSec Tunnnel and IKE Gateway. This skillet is meant to be an easy IPSec tunnel setup that can be replicated for SE POCs, customer environments where hundreds of tunnels need to be configured, and can be leveraged for on-prem tunnels, site-2-site tunnels, and cloud environments.  The skillet is also extensible in that it can be paired with other skillets designed to configure dynamic routing if dynamic tunnel routing is desired over static routing.  

Limitations: This particular skillet is designed to configure IPv4 routes and gateways and would need to be adapted to support IPv6. It is also designed to configure static tunnel routes, but dynamic configuration can be added using a dynamic routing skillet. Authentication is designed to be handled with a preshared key and if ProxyIDs are necessary, they must be added after the skillet is deployed.  Additionally, the tunnel interface is designed to be ‘unnumbered’, meaning it doesn’t have an IP address.  If an IP address is needed for the tunnel interface, to enable tunnel monitoring, for example, that must be added after the skillet is deployed.
The skillet supports use of the following variables, each of which have default values that support the most common tunnel configurations:

* ipsec_tunnel_name - Name for the IPSEC Tunnel
* ike_gateway_name - Name for the IKE Gateway
* ike_version - List of IKEv1, IKEv2, or IKEv2-Preferred
* local_interface - IKE Interface on the local firewall
* local_interface_address - IKE Interface address on the local firewall
* peer_address - IKE Peer Address
* preshared_key - Preshared Key in plaintext
* remote_network_tunnel_route - The Destination Network/CIDR routed into the IPSec tunnel.
* tunnel_interface - The tunnel interface (tunnel.Number)
* tunnel_interface_zone - Zone applied to the Tunnel Interface (must exist)
* tunnel_route_name - Name for the route-based tunnel route
* virtual_router_name - Name of the virtual router (must exist)
* vsys - VsysID