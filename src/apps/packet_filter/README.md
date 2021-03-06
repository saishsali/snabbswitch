# PacketFilter App (apps.packet_filter.packet_filter)

The `PacketFilter` app receives packets on the `input` port and transmits
conforming packets to the `output` port. In order to conform, a packet
must match at least one of the *filter rules* of the `PacketFilter`
instance.

![PacketFilter](.images/PacketFilter.png)

## Configuration

The `PacketFilter` app accepts a list of filter rules as its
configuration argument. A filter rule is a table in which each key/value
pair specifies a pattern to match against incoming packets. The following
keys are available:

— Key **ethertype**

*Required*. The ethernet type in use (IPv4 or IPv6). A string identifier,
either "ipv4" or "ipv6".

— Key **protocol**

*Optional*. The protocol is use (ICMP, UDP or TCP). A string identifier,
may be one of "icmp", "udp" or "tcp".

— Key **source_cidr**

— Key **dest_cidr**

*Optional*. Source and destination addresses. IP ranges in CIDR notation
as strings.

— Key **source_port_min**

— Key **source_port_max**

*Optional*. The source port range. Integers denoting the minimum and
maximum source port numbers. If only one is set then only that port is
allowed.

— Key **dest_port_min**

— Key **dest_port_max**

*Optional*. The destination port range. Integers denoting the minimum and
maximum destination port numbers. If only one is set then only that port
is allowed.

— Key **state_track**

*Optional*. Tracks connections state in a named connection table.  If used
inside a rule, every packet that passes this specific rule is tracked.
If used 'outside' any rule, packets passing _any_ rule on this app will be
tracked.

— Key **state_check**

*Optional*. Checks if a packet belongs to a connection in a named
connection table.  If used inside a rule, a packet must belong to an
existing connection in addition to any other condition in the rule to pass.
If used 'outside' any rule, if a packet belongs to an existing connection
it's enough to pass the app.
