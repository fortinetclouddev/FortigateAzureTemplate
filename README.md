This template set creates a vnet or uses an existing vnet of your selection.
This template set creates or uses two public IPs connected as frontends to an Azure public load balancer.
    Note: you also have an option to not use a public IP
This template set creates or uses a storage account
This template set creates 2 FortiGates

In order to configure FortiGates:
  FortiGate-A:
    Connect via https on port 9443 to public IP1 (ex: https://1.2.3.4:9443)
    Connect via SSH on port 22 to public IP1 to directly access the CLI
  FortiGate-B:
    Connect via https on port 9443 to public IP2  (ex: https://1.2.3.4:9443)
    Connect via SSH on port 22 to public IP2 to directly access the CLI

The Azure Load Balancer will be configured to forward ports 22,500,4500,and 9443(translated to 443) to the FortiGates individually.
The Azure Load Balancer will be configured to load balance ports 443 (translated to custom ports 1443 & 2443) and 80 (translated to port 80 and custom port 2080) for both public IPs.

You can use the VPN ports in a redundant fashion with this setup by configuring "dial-up" VPNs on the FortiGates.  However, if that's your purpose, it would be better to assign public IPs directly to the Network Interfaces in Azure.  This will create a 1:1 NAT to the assigned IP, and you can configure VPNs through those IP addresses.

See the included SessionSync and HA-Monitoring files for help with configuring session synchronization and redundant Azure routing.
