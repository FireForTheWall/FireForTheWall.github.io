# Tor Network

Tor, or "The Onion Router," is an overlay network (meaning it's a network built on top of another network, which in this case is the internet). The Tor Network isn't meant to be a censorship circumvention tool, but its design allows it to be used to bypass censorship as well. The main usage of this network is to enable its users to communicate anonymously within the network through layered routing and encryption.

Tor works by routing traffic through a series of volunteer nodes. This series of nodes is called a circuit in the Tor network. In a circuit, your data is encrypted to a random node called the entry node, then your data is encrypted to another random node called the middle node, and finally, your data is passed to a random node called the exit node. The encrypted data is peeled to reveal its content and destination, but because of this routing, the source of the traffic is unknown.

## How it works to bypass censorship

Because of the Tor network's layered routing and exit nodes (which route the Tor network's traffic to the [clearnet]()), Tor can act as a 3-layered VPN, meaning you will send your data to an entry node, and the data will be sent to the clearnet by an exit node that is very likely to have free access to the internet.

The problem is that the Tor network's traffic is detectable by firewalls and can be censored. Also, the entry nodes are known and can be censored using [IP filtering]() or [DNS Spoofing]() techniques. Because of this problem, Tor features some circumvention tools to bypass blocked access to the Tor network.

These circumvention tools are called "pluggable transports" or "bridges." They cannot usually be used directly to obfuscate normal traffic, and they must be used along with the Tor network (they can be used to obfuscate other traffic by some tweaks and modifications).

| Pluggable Transport | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| Obfs3               | Obfs3 is a pluggable transport meant to make traffic look random and not like any other protocol. Although Obfs3 is not supported anymore, it can be used to obfuscate other traffic such as SSH traffic or VPN traffic. |
| Obfs4               | It also makes Tor traffic look random while also preventing Obfs4 bridges from being found and censored through internet scanning, so they are less likely to be censored compared to Obfs3 bridges. |
| meek                | Meek transports make traffic look like you are browsing a major website. For example, meek-azure makes it look like you're using Microsoft services instead of Tor. |
| Snowflake           | Snowflake works by routing your traffic through volunteer-operated WebRTC proxies to make it look like you are on a video call instead of Tor. |
| WebTunnel           | WebTunnel makes your Tor traffic look like HTTPS website traffic. |

## Privacy and security measures

WIP

## Implementations

WIP

## How to use and set up

WIP
