Lesson 10: Explaining Network Services

Topic 10A: Explain the Use of Network Addressing Services

DYNAMIC HOST CONFIGURATION PROTOCOL

The Dynamic Host Configuration Protocol (DHCP) provides an automatic method for allocating an IP address, subnet mask, and optional parameters, such as the default gateway and DNS server addresses, when a host joins the network. All the major operating systems provide support for DHCP clients and servers. DHCP servers are also embedded in many SOHO routers and modems.

A host is configured to use DHCP by specifying in the TCP/IP configuration that it should automatically obtain an IP address.

DHCP Discover, Offer, Request, Ack process. (Images © 123RF.com.)

When a DHCP client initializes, it broadcasts a DHCPDISCOVER packet to find a DHCP server. All communications are sent using UDP, with the server listening on port 67 and the client on port 68.

Presuming it has an IP address available, the DHCP server responds to the client with a DHCPOFFER packet, containing the address and other configuration information.

While the client doesn't have an IP address yet, the DHCPOFFER is usually delivered as unicast because the server knows the client's MAC address. Some hosts cannot receive unicast without an IP address. They should set a broadcast bit in the DHCPDISCOVER packet.

The client may choose to accept the offer using a DHCPREQUEST packet-also broadcast onto the network.

Assuming the offer is still available, the server will respond with a DHCPACK packet. The client broadcasts an ARP message to check that the address is unused. If so, it will start to use the address and options; if not, it declines the address and requests a new one.

The IP address is leased by the server for a limited period only. A client can attempt to renew or rebind the lease before it expires. If the lease cannot be renewed, the client must release the IP address and start the discovery process again.

Sometimes, the DHCP lease process is called the DORA process: Discover, Offer, Request, and Ack(nowledge).

DHCP SERVER CONFIGURATION

DHCP is normally deployed as a service of a network operating system or through an appliance such as a switch or router. A DHCP server must be allocated a static IP address and configured with a range (or pool) of IP addresses and subnet masks plus option values to allocate.

Configuring DHCP on a TP-LINK wireless access point. (Screenshot courtesy of TP-Link Technologies Co., Ltd.)

A range of addresses and options configured for a single subnet is referred to as a scope. To define a scope, you must provide a start and end IP address along with a subnet mask. The server maintains a one-to-one mapping of scopes to subnets. That is, no scope can cover more than one subnet and no subnet can contain more than one scope.

The multifunction device shown only supports a single scope. The DHCP server must be placed in the same subnet as its clients. More advanced DHCP servers might be configured to manage multiple scopes. Where a server provides IP configuration for multiple subnets/scopes, it must choose the pool to service each request based on the subnet from which the request originated.

There is no mechanism for a client to choose between multiple servers. Therefore, if multiple DHCP servers are deployed-for fault tolerance, for instance-they must be configured with nonoverlapping or split scopes. DHCP for multiple subnets is usually handled by configuring relay agents to forward requests to a central DHCP server.

DHCP OPTIONS CONFIGURATION

Along with an address scope, you also need to define other parameters, such as lease time and options.

DHCP Lease Time and Available Leases

The client can renew the lease when at least half the lease's period has elapsed (T1 timer) so that it keeps the same IP addressing information. If the original DHCP server does not respond to the request to renew the lease, the client attempts to rebind the same lease configuration with any available DHCP server. By default, this happens after 87.5% of the lease duration is up (T2 timer). If this fails, the client releases the IP address and continues to broadcast to discover a server.

A long lease time means the client does not have to renew the lease often, but the DHCP server's available pool of IP addresses is not replenished frequently. Where IP addresses are in short supply, a short lease period enables the DHCP server to allocate addresses previously assigned to hosts that are now not active on the network.

A Windows client can be forced to release a lease by issuing a command such as ipconfig. In Linux, the utility dhclient is often used for this task, though modern distributions might use NetworkManager or systemd-networkd. A Windows host that fails to obtain a lease will revert to an automatic IP address (APIPA) or link-local configuration and select an address in the 169.254.0.0/16 range. Linux might use link-local addressing, set the address to unknown (0.0.0.0), or leave the interface unconfigured.

DHCP Options

When the DHCP server offers a configuration to a client, at a minimum it must supply an IP address and subnet mask. Typically, it will also supply other IP-related settings, known as DHCP options. Each option is identified by a tag byte or decimal value between 0 and 255 (though neither 0 nor 255 can be used as option values). Some widely used options include:

●	The default gateway (IP address of the router).

●	The IP address(es) of DNS servers that can act as resolvers for name queries.

●	The DNS suffix (domain name) to be used by the client.

●	Other useful server options, such as time synchronization (NTP), file transfer (TFTP), or VoIP proxy.

A set of default (global) options can be configured on a server-wide basis. Default options can be overridden by setting scope-specific options.

DHCP RESERVATIONS AND EXCLUSIONS

One disadvantage of the standard dynamic assignment method is that it does not guarantee that any given client will retain the same IP address over time. There are some cases where it would be advantageous for certain hosts, such as network printers or wireless access points, to retain their IP addresses.

One solution is to configure static assignments, using IP addresses outside the DHCP scope. Alternatively, statically assigned addresses can be assigned from a specially configured exclusion range, if this is supported by the server. While these solutions are functional, they lose the advantages of centralized configuration management.

An alternative approach is to create a reservation. A reservation is a mapping of a MAC address or interface ID to a specific IP address within the DHCP server's address pool. When the DHCP server receives a request from the given interface, it always provides the same IP address. This is also referred to as static or fixed address assignment. An automatically allocated reservation refers to an address that is leased permanently to a client. This is distinct from static allocation as the administrator does not predetermine which specific IP address will be leased.

DHCP RELAY AND IP HELPER

Normally, routers do not forward broadcast traffic. This means that each broadcast domain must be served by its own DHCP server. On a large network with multiple subnets, this would mean provisioning and configuring many DHCP servers. To avoid this scenario, a DHCP relay agent can be configured to provide forwarding of DHCP traffic between subnets. Routers that can provide this type of forwarding are described as RFC 1542 compliant.

The DHCP relay intercepts broadcast DHCP frames, applies a unicast address for the appropriate DHCP server, and forwards them over the interface for the subnet containing the server. The DHCP server can identify the original IP subnet from the packet and offer a lease from the appropriate scope. The DHCP relay also performs the reverse process of directing responses from the server to the appropriate client subnet.

Configuring a DHCP relay agent. (Images © 123RF.com)

This IP helper functionality can be configured on routers to allow set types of broadcast traffic (including DHCP) to be forwarded to an interface. The IP helper function supports the function of the DHCP relay agent. For example, in the diagram, hosts in the 10.1.20.0/24 and 10.1.10.0/24 subnets need to use a DHCP server for autoconfiguration, but the DHCP server is located in a different subnet. The router is configured as a DHCP relay agent, using the following commands to enable forwarding of DHCP broadcasts on the interfaces serving the client subnets:

interface eth1

ip helper-address 10.1.0.200

interface eth2

ip helper-address 10.1.0.200

UDP forwarding is a more general application of the same principle. As well as DHCP, it is used for the Network Time Protocol (NTP) and other broadcast-based applications.

DHCPV6 SERVER CONFIGURATION

IPv6's Stateless Address Autoconfiguration (SLAAC) process can locate routers (default gateways) and generate a host address with a suitable network prefix automatically. In this context, the role of a DHCP server in IPv6 is different. DHCPv6 is often just used to provide additional option settings, rather than leases for host IP addresses. The format of messages is different, but the process of DHCP server discovery and address leasing (if offered) is fundamentally the same. As IPv6 does not support broadcast, clients use the multicast address ff02::1:2 to discover a DHCP server. DHCPv6 uses ports 546 (clients) and 547 (servers), rather than ports 68 and 67 as in DHCPv4.

In stateless mode, a client obtains a network prefix from a Router Advertisement and uses it with the appropriate interface ID. The router can also set a combination of flags to tell the client that a DHCP server is available. If so configured, the client solicits a DHCPv6 server using the multicast address ff02::1:2 and requests additional configuration information.

DHCPv6 stateless mode. (Images © 123RF.com.)

By contrast, stateful mode means that a host can also obtain a routable IP address from a DHCPv6 scope, plus any other options (like with DHCP for IPv4).

DHCPv6 stateful mode. (Images © 123RF.com.)

Configuring the scope requires you to define the network prefix and then any IP addresses that are to be excluded from being offered. All other addresses that are not explicitly excluded can be offered. The host must still listen for a router advertisement to obtain the network prefix and configure a default gateway. There is no mechanism in DHCPv6 for setting the default route.

Topic 10B: Explain the Use of Name Resolution Services

HOST NAMES AND FULLY QUALIFIED DOMAIN NAMES

The Internet Protocol uses a binary IP address to locate a host on an internetwork. The dotted decimal (IPv4) or hex (IPv6) representation of this IP address is used for configuration purposes, but it is not easy for people to remember. For this reason, a "friendly" name is also typically assigned to each host. There are two types of names: host names and Fully Qualified Domain Names (FQDNs).

A host name is assigned to a computer by the administrator, usually when the OS is installed. The host name needs to be unique on the local network.

To avoid the possibility of duplicate host names on the Internet, a fully qualified domain name (FQDN) is used to provide a unique identity for the host belonging to a particular network. An example of an FQDN might be nut.widget.example. An FQDN is made up of the host name and a domain suffix. In the example, the host name is nut and the domain suffix is widget.example. This domain suffix consists of the domain name widget within the top-level domain (TLD) .example . A domain suffix could also contain subdomains between the host and domain name. The trailing dot or period represents the root of the hierarchy.

When you are configuring name records, an FQDN must include the trailing period to represent the root, but this can be omitted in most other use cases.

A domain name must be registered with a registrar to ensure that it is unique within a top-level domain. Once a domain name has been registered, it cannot be used by another organization. The same domain name may be registered within different top-level domains, however-widget.example. and widget.example.uk. are distinct domains, for instance.

Numerous hosts may exist within a single domain. For example: nut, bolt , and washer might all be hosts within the widget.example. domain. Given that, FQDNs must follow certain rules:

●	The host name must be unique within the domain.

●	The total length of an FQDN cannot exceed 253 characters, with each label (part of the name defined by a period) no more than 63 characters (excluding the periods).

●	A DNS label should use letter, digit, and hyphen characters only. A label should not start with a hyphen. Punctuation characters such as the period (.) or forward slash (/) should not be used.

●	DNS labels are not case-sensitive.

Additionally, Internet registries may have their own restrictions.

DOMAIN NAME SYSTEM

The Domain Name System (DNS) is a global hierarchy of distributed name server databases that contain information on domains and hosts within those domains. At the top of the DNS hierarchy is the root, which is represented by the null label, consisting of just a period (.). There are 13 root level servers (A to M).

Immediately below the root lie the top-level domains (TLDs). There are several types of top-level domains, but the most prevalent are generic (such as .com, .org, .net, .info, .biz), sponsored (such as .gov, .edu), and country code (such as .uk, .ca, .de). DNS is operated by ICANN (icann.org), which also manages the generic TLDs. Country codes are generally managed by an organization appointed by the relevant government.

Information about a domain is found by tracing records from the root down through the hierarchy. The root DNS servers have complete information about the top-level domain servers. In turn, these servers have information relating to servers for the second level domains. No name server has complete information about all domains. Records within the DNS tell them where an authoritative name server for the missing information is found.

DNS hierarchy. (Images © 123RF.com.)

An FQDN reflects this hierarchy, from most specific on the left (the host's resource record with its name:IP address mapping) to least specific on the right (the TLD followed by the root). For example: pc.corp.515support.com.

NAME RESOLUTION USING DNS

The signal for the name resolution process to commence occurs when a user presents an FQDN (often within a web address) to an application program, such as a web browser. The client application, referred to as a stub resolver, checks its local cache for the mapping. If no mapping is found, it forwards the query to its local name server. The IP addresses of one or more name servers that can act as resolvers are usually set in the TCP/IP configuration. The resolution process then takes place as follows:

DNS name resolution process. (Images © 123RF.com.)

Most queries between name servers are performed as iterative lookups. This means that a name server responds to a query with either the requested record or the address of a name server at a lower level in the hierarchy that is authoritative for the namespace. It makes no effort to try to make additional queries to locate information that it does not have. In the figure, at steps 4 and 5, the root server and .net name server simply pass the querying server the address of an authoritative name server. They do not take on the task of resolving the original query for www.515web.net.

A recursive lookup means that if the queried server is not authoritative, it does take on the task of querying other name servers until it finds the requested record or times out. The name servers listed in a client's TCP/IP configuration accept recursive queries. This is the type of querying performed by the corp.515support.com name server.

A DNS server may be configured to only perform recursive querying (a resolver), or it may perform both recursive querying and maintain zone records, or it may only maintain zone records. Usually the roles are split, especially if the servers are open to the Internet. Most Internet-accessible DNS servers disable recursive queries. Recursive resolvers are typically only accessible by authorized clients-subscribers within an ISP's network or clients on a private LAN, for instance.

RESOURCE RECORD TYPES

A DNS zone will contain numerous resource records. These records allow a DNS name server to resolve queries for names and services hosted in the domain into IP addresses. Resource records can be created and updated manually (statically), or they can be generated dynamically from information received from client and server computers on the network.

The Start of Authority (SOA) record identifies the primary authoritative name server that maintains complete resource records for the zone. The primary name server can be used to modify resource records. The SOA also includes contact information for the zone and a serial number for version control.

Configuring a Start of Authority record in Windows DNS. (Screenshot courtesy of Microsoft.)

Name Server (NS) records identify authoritative DNS name servers for the zone. As well as the primary name server, most zones are configured with secondary name servers for redundancy and load balancing. Secondary name servers hold read-only copies of resource records but can still be authoritative for the zone.

Resource records configured on a BIND DNS server.

HOST ADDRESS AND CANONICAL NAME RECORDS

An address (A) record is used to resolve a host name to an IPv4 address. An AAAA record resolves a host name to an IPv6 address.

Both types of host records (A and AAAA) plus a CNAME record in Windows Server DNS. (Screenshot courtesy of Microsoft.)

DNS uses the UDP transport protocol over port 53 by default, and UDP has a maximum packet size of 512 bytes. Due to the much larger address sizes of IPv6, AAAA records can exceed this size. This can result in UDP packets being fragmented into several smaller packets. This can result in these packets being blocked by firewalls if they are not configured to expect them. Network administrators should check that their DNS servers can accept these transmissions and that intermediary components are not blocking them.

A Canonical Name (CNAME) (or alias) record is used to configure an alias for an existing address record (A or AAAA). For example, the IP address of a web server with the host record lamp could also be resolved by the alias www . CNAME records are also often used to make DNS administration easier. For example, an alias can be redirected to a completely different host temporarily during system maintenance.

Multiple different named resource records can refer to the same IP address (and vice versa in the case of load balancing).

There is nothing to stop an administrator configuring multiple address records to point different host names to the same IP address. Using CNAME records is usually considered better practice, however. It is also possible to configure multiple A or AAAA records with the same host name but different IP addresses. This is usually done as a basic load balancing technique, referred to as round robin DNS.

MAIL EXCHANGE, SERVICE, AND TEXT RECORDS

A Mail Exchange (MX) record is used to identify an email server for the domain. In a typical network, multiple servers are installed to provide redundancy, and each one will be represented with an MX record. Each server record is given a preference value with the lowest numbered entry preferred. The host identified in an MX record must have an associated A or AAAA record. An MX record must not point to a CNAME record.

While most DNS records are used to resolve a name into an IP address, a Service (SRV) record contains the service name and port on which a particular application is hosted. SRV records are often used to locate VoIP or media servers. SRV records are also an essential part of the infrastructure supporting Microsoft’s Active Directory; they are used by clients to locate domain controllers, for instance. As with MX, SRV records can be configured with a priority value.

SRV records in Windows Server DNS. (Screenshot courtesy of Microsoft.)

A TXT record is used to store any free-form text that may be needed to support other network services. A single domain name may have many TXT records, but most commonly they are used as part of Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM). An SPF record is used to list the IP addresses or names of servers that are permitted to send email from a particular domain and is used to combat the sending of spam. DKIM records are used to decide whether you should allow received email from a given source, preventing spam and mail spoofing. DKIM can use encrypted signatures to prove that a message really originated from the domain it claims.

POINTER RECORDS

A DNS server may have two types of zones: forward lookup and reverse lookup. Forward lookup zones contain the resource records listed previously. For example, given a name record, a forward lookup returns an IP address; an MX record returns a host record associated with the domain's mail services. Conversely, a reverse DNS query returns the host name associated with a given IP address. This information is stored in a reverse lookup zone as a pointer (PTR) record.

Reverse lookup zone and pointer records in Windows Server DNS. (Screenshot courtesy of Microsoft.)

Reverse DNS querying uses a special domain named by the first three octets of IP addresses in the zone in reverse order and appended with in-addr.arpa. The name server is configured with a reverse lookup zone . This zone contains PTR records consisting of the final octet of each host record. For example, the reverse lookup for a host record containing the IP address 198.51.100.1 is:

1\.100.51.198.in-addr.arpa

IPv6 uses the ip6.arpa domain; each of the 32 hex characters in the IPv6 address is expressed in reverse order as a subdomain. For example, the IPv6 address:

2001:0db8:0000:0000:0bcd:abcd:ef12:1234

is represented by the following pointer record:

4\.3.2.1.2.1.f.e.d.c.b.a.d.c.b.0.0.0.0.0.0.0.0.0.8.b.d.0.1.0.0.2.ip6.arpa

Reverse lookup zones are not mandatory and are often omitted from DNS servers, as they can be used by hackers to sequentially work through a range of IP addresses to discover useful or interesting device names, which can then be targeted by other hacking mechanisms.

Topic 10C: Configure DNS Services

DNS SERVER CONFIGURATION

DNS is essential to the function of the Internet. Windows Active Directory® and most Linux networks also require a DNS service to be running and correctly configured. It is important to realize that there are different kinds of DNS servers however, fulfilling different roles in network architecture.

DNS Server Types

A DNS server is usually configured to listen for queries on UDP port 53. Some DNS servers are also configured to allow connections over TCP port 53, as this allows larger record transfers (over 512 bytes). Larger transfers might be required if IPv6 is deployed on the network or if the DNS servers are using a security protocol (DNSSEC).

DNS name servers maintain the DNS namespace in zones. A single zone namespace might host records for multiple domains. A single name server might be configured to manage multiple zones. A name server can maintain primary and/or secondary zones:

●	Primary means that the zone records held on the server are editable. A zone can be hosted by multiple primary servers for redundancy. As the zone records are editable on all primaries, changes must be carefully replicated and synchronized. It is critically important to update the serial number for each change.

●	Secondary means that the server holds a read-only copy of the zone. This is maintained through a process of replication known as a zone transfer from a primary name server. A secondary zone would typically be provided on two or more separate servers to provide fault tolerance and load balancing. Again, the serial number is a critical part of the zone transfer process.

The noninclusive terms "master" to mean primary and "slave" to mean secondary are used in some DNS server versions. This type of terminology is deprecated in the latest versions.

A name server that holds complete records for a domain can be defined as authoritative. This means that a record in the zone identifies the server as a name server for that namespace. Both primary and secondary name servers are authoritative.

Servers that don't maintain a zone (primary or secondary) are referred to as cache-only servers. A non-authoritative answer from a server is one that derives from a cached record, rather than directly from the zone records.

DNS Caching

Each resource record can be configured with a default time to live (TTL) value, measured in seconds. This value instructs resolvers how long a query result can be kept in cache. Setting a low TTL allows records to be updated more quickly but increases load on the server and latency on client connections to services. Some common TTL values include 300 (5 minutes), 3,600 (1 hour), 86,400 (1 day), and 604,800 (1 week).

DNS caching is performed by both servers and client computers. In fact, each application on a client computer might be configured to manage its own DNS cache. For example, separate web browser applications typically maintain their own caches rather than relying on a shared OS cache.

If there is a change to a resource record, server and client caching means that the updated record can be relatively slow to propagate around the Internet. These changes need to be managed carefully to avoid causing outages. Planning for a record change involves reducing the TTL in the period before the change, waiting for this change to propagate before updating the record, and then reverting to the original TTL value when the update has safely propagated.

INTERNAL VERSUS EXTERNAL DNS

As well as making sure that resource records for the managed domain(s) are accurate, administrators should ensure that DNS services are highly available and secure, to prevent DNS spoofing, where an attacker is able to supply false name resolutions to clients.

A company will use primary and secondary name servers to maintain authoritative zone records for the domains that it manages. Internal DNS zones refer to the domains used on the private network only. These name records should only be available to internal clients. For example, a company might run a Windows Active Directory network using the domain name corp.515support.com. The zone records for the subdomain corp.515support.com would be served from internal name servers. This would allow a client PC ( pc1.corp.515support.com ) to contact a local application server ( crm.corp.515support.com ). The name servers hosting these internal subdomain records must not be accessible from the Internet.

External DNS zones refer to records that Internet clients must be able to access. For example, the company might run web and email services on the domain 515support.com. In order for Internet hosts to use a web server at www.515support.com or send email to an @515support.com address, the zone records for 515support.com must be hosted on a name server that is accessible over the Internet.

Companies must also provide name resolution services to support their internal clients contacting other domains. The function of a resolver is to perform recursive queries in response to requests from client systems (stub resolvers). If a name server is not authoritative for the requested domain, it can either perform a recursive query to locate an authoritative name server or it can forward the request to another name server. A recursive resolver must be configured with a root hints file so that it can query the whole DNS hierarchy from the root servers down. DNS servers should allow recursive queries only from authorized internal clients. It is also a good idea to separate the DNS servers used to host zone records from ones used to service client requests for non authoritative domains.

It is possible for the same DNS server instance to perform in both name server and resolver roles, but more typically these functions are separated to different servers for security reasons.

As an alternative to recursion (or to supplement it), name servers can be configured to resolve queries via forwarding. A forwarder transmits a client query to another DNS server and routes the replies it gets back to the client. A conditional forwarder performs this task for certain domains only. For example, you might configure a DNS server that is authoritative for the local private network (internal DNS), but that forwards any requests for Internet domains to an external DNS resolver run by your ISP.

NSLOOKUP

Name resolution troubleshooting typically involves testing multiple clients and servers. The use of caching and the distributed nature of the system means that configuration errors can occur in several different places.

You might start investigating a name resolution issue by verifying the name configured on a host. In Windows, you can use the command ipconfig /all to display the FQDN of the local host. In Linux, you can use the command hostname --fqdn .

In a Windows environment, you can troubleshoot DNS name resolution with the nslookup command:

nslookup -Option Host DNSServer

Host can be either a host name, domain name, FQDN, or IP address. DNSServer is the IP address of a server used to resolve the query; the default DNS server is used if this argument is omitted. Option specifies an nslookup subcommand. For example, the following command queries Google's public DNS server (8.8.8.8) for information about 515support.com's mail records:

nslookup -type=mx 515support.com 8.8.8.8

If nslookup is run without any arguments (or by specifying the server only with nslookup – DNSServer ), the tool is started in interactive mode. You can perform specific query types and output the result to a text file for analysis.

The first two nslookup commands identify comptia.org's MX and primary name server records using Google's public DNS resolver (8.8.8.8). Note that the answers are nonauthoritative. The third command queries CompTIA's name server for the MX record. This answer is authoritative. (Screenshot courtesy of Microsoft.)

The Windows PowerShell environment provides a more sophisticated scripted environment that you can use to issue cmdlets to test DNS name resolution (and change DNS settings as well, if required). PowerShell® provides a cmdlet called Resolve-DnsName, which allows a more flexible method of testing name resolution than nslookup, as it allows testing of the different methods of name resolution (HOSTS file, DNS cache, and DNS server).

DIG

Domain Information Groper (dig) is a command-line tool for querying DNS servers that ships with the BIND DNS server software published by the Internet Systems Consortium (ISC) (isc.org/downloads/bind).

dig can be run pointing at a specific DNS server; otherwise, it will use the default resolver. Without any specific settings, it queries the DNS root zone. A simple query uses the syntax: dig host . This will search for the address record for the host, domain, or FQDN or PTR record for an IP address.

The following command example directs the resolve request to the specific DNS server identified after the @ symbol. This can be an FQDN or IP address.

dig @ns1.isp.example host

Other examples of dig are to display all the resource records about a domain or just specific ones such as Mail Exchange:

dig @ns1.isp.example host all

dig @ns1.isp.example host MX

dig often generates a lot of information, so it is possible to add parameters to the end of the command like +nocomments or +nostats , which will reduce the output.

Using dig to locate MX and A records.

You can install dig on Windows by downloading the BIND DNS server package and installing it using the tools-only option.
