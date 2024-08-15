# Tor Network

Tor, or "The Onion Router," is an overlay network (meaning it's a network built on top of another network, which in this case is the internet). The Tor Network isn't meant to be a censorship circumvention tool, but its design allows it to be used to bypass censorship as well. The main usage of this network is to enable its users to communicate anonymously within the network through layered routing and encryption. [^1]

Tor works by routing traffic through a series of volunteer nodes. This series of nodes is called a circuit in the Tor network. In a circuit, your data is encrypted to a random node called the entry node, then your data is encrypted to another random node called the middle node, and finally, your data is passed to a random node called the exit node. The encrypted data is peeled to reveal its content and destination, but because of this routing, the source of the traffic is unknown. [^2]

## How it works to bypass censorship

Because of the Tor network's layered routing and exit nodes (which route the Tor network's traffic to the [clearnet]()), Tor can act as a 3-layered VPN, meaning you will send your data to an entry node, and the data will be sent to the clearnet by an exit node that is very likely to have free access to the internet.

The problem is that the Tor network's traffic is detectable by firewalls and can be censored. Also, the entry nodes are known and can be censored using [IP filtering]() or [DNS Spoofing]() techniques. Because of this problem, Tor features some circumvention tools to bypass blocked access to the Tor network.

These circumvention tools are called "pluggable transports" or "bridges." They cannot usually be used directly to obfuscate normal traffic, and they must be used along with the Tor network (they can be used to obfuscate other traffic by some tweaks and modifications). [^3]

| Pluggable Transport | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| [Obfs3]()           | Obfs3 is a pluggable transport meant to make traffic look random and not like any other protocol. Although Obfs3 is not supported anymore, it can be used to obfuscate other traffic such as SSH traffic or VPN traffic. |
| [Obfs4]()           | It also makes Tor traffic look random while also preventing Obfs4 bridges from being found and censored through internet scanning, so they are less likely to be censored compared to Obfs3 bridges. |
| [meek]()            | Meek transports make traffic look like you are browsing a major website. For example, meek-azure makes it look like you're using Microsoft services instead of Tor. |
| [Snowflake]()       | Snowflake works by routing your traffic through volunteer-operated WebRTC proxies to make it look like you are on a video call instead of Tor. |
| [WebTunnel]()       | WebTunnel makes your Tor traffic look like HTTPS website traffic. |

## Privacy and Security Measures

Tor network's communications are encrypted and secure, meaning your ISP (Internet Service Provider) cannot decrypt the content of the messages and data passing through. But they can detect that you are using Tor if it is not used with a pluggable transport such as Obfs4 or Snowflake, due to a few reasons:

- [Traffic analysis]() can be used to detect and block Tor connections based on unique characteristics of Tor network's packets, such as packet sizes (Tor has a fixed length for its cell sizes), timing, and encrypted patterns.
- [Deep Packet Inspection (DPI)]() can be used to inspect the fully encrypted data and find specific patterns associated with Tor network's communications.
- Tor has a public list of its entry nodes and exit nodes, which can be easily blocked by firewalls.

Also, if the Tor network is used to access the clearnet, meaning the destination of requests is not inside the Tor network (for example, duckduckgo.com is a clearnet, or normal internet website, and duckduckgogg42xjoc72x3sjasowoarfbgcmvfimaftt6twagswzczad.onion is a Tor network website), the exit node will be able to see the data that it is passing to the destination. But this is less of a problem now that most websites use HTTPS for encryption, leaving only some small metadata for exit nodes to see. And also, when they see the data, they cannot know where it came from.

## Implementations

There are two official core implementations of Tor: one is the Tor implemented in the C programming language, and the other is Arti[^4] implemented in Rust. The Rust implementation is not fully ready yet, and it is suggested to use the C implementation for actual privacy reasons.

Also, there are clients built based on these core implementations for different operating systems:

| Implementation                                               | Description                                                  | Windows | Linux | Android | iOS  | macOS |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------- | ----- | ------- | ---- | ------ |
| [C Tor](https://www.torproject.org/download/tor/)            | Core implementation of Tor, which can be used to run volunteer nodes, a server, or a client. | Yes     | Yes   | Yes     | No   | Yes    |
| [Arti](https://crates.io/crates/arti)                        | Rust version of the C Tor implementation, *not ready to use yet.* | Yes     | Yes   | Yes     | No   | Yes    |
| [Tor Browser](https://www.torproject.org/download/) (or "[Onion Browser](https://onionbrowser.com/)") | A hardened browser with fingerprint-resisting features and Tor network built-in. | Yes     | Yes   | Yes     | Yes  | Yes    |
| [Orbot](https://orbot.app/en/download/)                      | A free and open-source front-end for Tor, allowing the use of Tor as a VPN or a proxy. | No      | No    | Yes     | Yes  | No     |

## How to use and set up

WIP

---

[^1]: For more detailed information: [https://spec.torproject.org/intro/index.html](https://spec.torproject.org/intro/index.html)  
[^2]: How Tor path and circuit work: [https://spec.torproject.org/path-spec/general-operation.html](https://spec.torproject.org/path-spec/general-operation.html)  
[^3]: Pluggable transports specifications: [https://spec.torproject.org/pt-spec/index.html](https://spec.torproject.org/pt-spec/index.html)  
[^4]: Announcing Arti: [https://blog.torproject.org/announcing-arti/](https://blog.torproject.org/announcing-arti/)
