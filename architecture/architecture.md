# Architecture

## Traditional Remote Access Deployments

A traditional remote access solution usually is some sort of VPN service. Users log into the VPN (hopefully via 2FA) via a client of some sort, and they are given an IP and access to the network. Strictly speaking, these services allow access to IPs via protocol/port (example: allow access 192.168.1.1 over TCP/443). Some VPN solutions can also enforce endpoint checks to allow/deny access based on some sort of compliance framework. The most commonly-used framework is called **Trusted Network Computing** (TNC) can be found on the Trust Computing Group's [website](https://trustedcomputinggroup.org/work-groups/trusted-network-communications/tnc-resources/).

For simple use-cases, this is often *good enough* to gain access to resources. However, this starts falls apart in several scenarios:

* What happens if a server hosts multiple websites? How do you discern access to *Application A*, but deny access to *Application B* that listens on the same IP, Protocol, and Port?
* What happens if the server changes IPs? That's at minimum a configuration change, and depending on the VPN client it may require users to log out of the VPN and log back in.
* Lastly, how do you manage access to cloud-based services? Are users bypassing the VPN (and likely - 2FA, security controls, etc.) altogether? Or are users backhauling all their traffic to the head-end office, causing access to trombone across the Internet?

## Next-Generation Remote Access Deployments

Next-Generation Access solutions slightly changed the remote access solution, rather than just allowing IP/Port/Protocol, we can add additional attributes, such as username/user group membership, and some sort of deep inspection on applications, such as looking at packet payload to determine which website a user is accessing; which is beyond the traditional Remote Access Deployment. However this approach still has its shortcomings.

Access based on username often **really** means *map user to an IP and allow access to application from that source IP*. If a user changes IPs for whatever reason, the network device will need to re-map the user to the new IP. This may interrupt traffic for the end-user. Most network devices allow access for already-opened sessions for a short amount of time. If an end-user's device gets stolen, denying access may take minutes or hours depending on the company's lost asset protocol.

Application inspection will allow a network device to determine valid hostnames/FQDNs for shared servers. Depending on the vendor, this often cuts performance on the network device considerably. If the resource is encrypted, say via TLS or SSH tunnels, then some sort of decryption/man-in-the-middle attack may need to be deployed or configured on the network device. This kills performance as well as adds to both cost and complexity to the remote access solution.

Lastly, application inspection means you will need to maintain a list of signatures that will be allowed/denied for a particular user. As you reach the hundreds or thousands of application definitions this becomes an untenable situation to manage. Besides, given the awful state of automation in the network security realm, how would you allow applications to self-register themselves into such a service?

## Enter Zero Trust
