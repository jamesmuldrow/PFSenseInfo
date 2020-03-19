# PFSenseInfo
Info related to PFSense Deployment

# OpenVPN Firewall Configurations

### The following information is provided for configuring PFSense firewalls in the environment.

## Initial Setup

1. Browse to public IP of range Firewall. Ip can be identified in portal.azure.com under "All resources / publicip".

2. Log in using username and password identified in terraform script.

3. Complete setup

4. Upon completion, the firewall will restart.

## OpenVPN Setup

1. Browse to: VPN > OpenVPN > Wizards
    - Type of server: Local User Access
    - Click Next

2. Create a New Certificate Authority (CA) Certificate
    - Descriptive name: Set descriptive name
    - Country Code: Set Country Code
    - State or Province: Set State or Province
    - City: Set City
    - Organization: Set Orginazation
    - Click "Add New CA"

3. Create a New Server Certificate
    - Descriptive name: Set descriptive name
    - Country Code: Set Country Code
    - State or Province: Set State or Province
    - City: Set City
    - Organization: Set Orginazation
    - Click "Create new Certificate"

4. General OpenVPN Server Information
    - Description: Set description

5. Tunnel Settings
    - Tunnel Network: Set tunnel network: 10.10.0.0/24
        - This is the virtual network used for private communications between this server and client hosts expressed using CIDR notation (eg. 10.0.8.0/24). The first network address will be assigned to the server virtual interface. The remaining network addresses will be assigned to connecting clients.

    - Redirect Gateway: Check redirect Gateway 
        - Force all client generated traffic through the tunnel

    - Local Network: Set local network that you want access to: 10.10.80.0/24
        -    This is the network that will be accessible from the remote endpoint, expressed as a CIDR range. This may be left blank if not adding a route to the local network through this tunnel on the remote machine. This is generally set to the LAN network.

    - Concurrent Connections: Set how many connections you want simultaniously. 50

    - Click "Next"

6. Traffic from clients to server
    - Firewall Rule: Check this box

7. Traffic from clients through VPN
   - OpenVPN rule: Check this box 
   - Click "Next"

8. Finished
    - Click "Finish"

## User Setup
1. Browse to https://xx.xx.xx.xx/system_usermanager.php
2. Click "Add"
3. Disabled: Click box to disable Firewall login
4. Username: set username
5. Password: Set Password & Confirm Password
6. Full Name: Set full name
7. Certificate: Click to create a user certificate
8. Descriptive name: Set User Cert name
9. Click "Save"

## OpenVPN Client Export
1. Browse to System > Package Manager > Available Packages
2. Search term: openvpn-client-export
3. Click "Install"
4. Click "Confirm"
5. Browse to VPN > OpenVPN > Client Export
6. OpenVPN Clients: Download appropriate VPN configs
