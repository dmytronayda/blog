---
layout: post
title: How does the Internet work?
description: A rather long article that reviews what the Internet is and how does it function
---
# What is the Internet?

The Internet is not controlled by government (or at least your Mr. or Mrs. President does not have the switch to turn it off in your local &quot;White House&quot; ), it&#39;s not a mythical &quot;cyberspace&quot;, and not &quot;magic&quot;. It is quite tangible and, at its essence, is a combination of physical network and sets of rules that control how that network operates. According to the &quot;Web IQ&quot; quiz conducted by the Pew Research Center 77 % of Americans think that the Internet and the World Wide Web are the same (What Internet Users Know About Technology and the Web, 2014). The Internet is an infrastructure that enables network communication: it is both the physical network and protocols that control it.

# Physical Network

### How is the information transferred from A to B in the network?

In context of the physical network, the data that is being transferred is just a list of ones and zeros - bits.

There are 3 ways to transfer bits over the network:

- Electricity – normal Ethernet wire. Cheap but has a considerable signal loss.
- Light – fiber optic cable. It is fast and does not have signal loss, but also expensive and hard to work with.
- Radio waves – this is how the WiFi and mobile Internet actually works. These are totally mobile but have a rather short range.

#### Limitations of the physical network

There two main characteristics of the physical network: bandwidth and latency.

Bandwidth is the measure of the transmission capacity. It&#39;s measured by bit rate. In other words, how many bits of data can be transferred over the network in a given period of time.

Latency is the measure of the delay. It&#39;s measured in seconds. In other words, how much time it takes one bit to travel from point A to point B in the network.

### General Picture of Network Infrastructure

#### Most Basic Level

At the most basic level the network is the two network enabled devices – say, two laptops in your household – that are connected to each other with a cable. The physical network in this case consists of:

1. 2 laptops;
2. and, a connecting cable.

However, connecting two devices together with the cable does not enable them to transfer data. This setup or set of instructions that allow the devices to communicate with each other is what makes the picture complete.

That is, our simplified Network looks more like this:

1. 2 laptops
2. connecting cable
3. and a set of rules that enables the communication

![2-laptops](/assets/images/2laptops.png)

#### Local Area Network

Zooming out from the most basic network, a more widely spread example of a network would be Local Area Network (LAN). In this case we connect multiple network devices with one another. Your home network is most likely using the Wireless LAN (WLAN). Local in LAN refers to the coverage limitations of the network. Be it wireless or wired LAN, it can cover only limited number of the network devices.

We can create LAN by connecting multiple laptops, PCs, etc. together using the networking device called [switch](https://en.wikipedia.org/wiki/Network_switch). This is a piece of networking hardware that connects devices on the network by utilizing their Media Access Control (MAC) addresses to forward the data.

This is how the LAN and WLAN can be displayed as a diagram:

![lan-network](/assets/images/lan-network.png)

#### Inter-network Communication

If we continue to zoom out to see the bigger picture, we would be able to see how Networks communicate with one another. They do that with the use of networking devices called routers.

Routers perform the traffic directing functions and act as entry / exit point to any given LAN.

![inter-network](/assets/images/inter-network.png)

#### Internet

If we zoom out even more, we can get the feeling of what the physical Internet infrastructure really is – a network of networks with millions of cables, routers, switches and hosts devices.

![internet](/assets/images/internet.png)

# Protocols

## Definition

Protocol is a set of rules governing the exchange or transmission of data (Protocols, 2020).

There are many protocols governing the network communication. The reason for this is that different protocols are either addressing different aspects of the network communication or designed to handle specific use-case.

## Layered System

The [Internet Protocol Suite](https://en.wikipedia.org/wiki/Internet_protocol_suite) is the conceptual model that is used to better understand what is happening on each layer of the network communication. The model consists of 4 layers:

1. Application
2. Transport
3. Internet
4. Link

The general idea of data transfer from level to level stays the same: protocol of the lower layer hides all the data it receives from the layer above within the data payload and adds some protocol specific header. The data payload and the headers form a Protocol Data Unit (PDU).

For example, the IP layered system would look something in following lines:
![ip-layered-system](/assets/images/layered-system-ip-model.png)


#### Application Layer
> - most commonly used protocol is HTTP (hypertext transfer protocol)
> - mainly concernted with the client-server communication
> - PDU is called an HTTP request / response
>   - HTTP *request* is required to have:
>     - request line: HTTP method, HTTP version, path
>     - `Host` header 
>     - optionally can also include other header data and message body
>   - HTTP *response* is required to have:
>     - response line: status code / text
>     - response headers and message body are optional 

#### Transport Layer ⬆️
> - most commonly used protocols TCP and UDP
> - mainly concerned with the communication between different application processes
> - TCP's PDU is called TCP **Segment**
>   - Headers contain source and destination socket (combination of IP address and a port number), connection status flags, etc.
>   - Data payload contains the data from the layers above

#### Internet Layer ⬆️
> - most common uses IP protocol
> - mainly concerns itself with inter-network communication between devices via the use of IP addressing
> - PDU is called an IP **Packet**
>   - Headers contain the source and destination IP addresses
>   - Data payload contains the data from the layers above

#### Link layer ⬆️
> - most commonly uses Ethernet protocol 
> - mainly concerns itself with local-network communication between devices via MAC (media access control) addressing
> - PDU is called an Ethernet **Frame**
>   - Headers contain source and destination MAC addresses
>   - Data payload contains the data from the layers above

## Link Layer

Let&#39;s have a closer look at what is happening on the lowest level of the Internet Protocol Suite model – Link Layer. This is the lowest layer at which encapsulation takes place.

### Purpose

The protocols of this layer are designed to tackle two tasks:

- Identify the devices on the physical network
- Move the data over the physical network between the devices

### Protocol governing the Link Layer

#### Ethernet

Ethernet is the most common protocol that is used at the Link Layer. It encapsulates the data it receives from the layer above into the PDU called Ethernet Frame.

The Header of the frame has source device address and destination device address. The Data Payload consist of whatever data is received from the layer above.

#### Main features of the Ethernet:

- Defining the host device within a LAN via MAC addressing
- Encapsulation of data into Ethernet Frames

#### MAC Addresses

Each network-enabled device – be it cellphone, iPad or coffee machine – all have the uniquely assigned code. This code, which is called a Media Access Control (MAC) address, is assigned to the device by a manufacturer and usually does not change.

You can find it in your machine System Preferences -\&gt; Ethernet Cards:

![mac-address](/assets/images/mac-address.png)

## The Internet Layer Protocol: IP

The Internet layer receives the data from the layer above: Transport layer.

### Purpose

The protocols of this layer are designed to tackle one primary task:

- Facilitate the communication between hosts (network enabled devices) on different networks.

### Protocol governing the Internet Layer

#### Internet Protocol (IP)

IP is the most common protocol that is used at the Internet Layer. It encapsulates the data it receives from the layer above into the PDU called a _packet_.

#### Main features of the IP:

- Routing capability via IP addressing
- Encapsulation of data into packets

**The Header** of the packet has source device IP address and a destination device IP address. Other header metadata includes protocol, which was used at the transport layer above, time to live, IP version used, fields related to fragmentation, etc.

**The Data Payload** consist of whatever data is received from the Transport layer above.

### IP Address

All devices on the Internet have a unique address: IP Address.

The IP address is logical and are assigned to all new devices in the current LAN. The IP address might look something similar to this:

![ip-address](/assets/images/ip-address.png)

In other words, when you want to visit a website and type in a URL, what you are really doing is typing the string that is associated with some IP address – the Internet Protocol address of your website.

How does the browser know the IP address of the website? It needs some kind of &quot;phone book&quot; to look it up.

### DNS

Domain Name System (DNS) associates names like [www.google.com](http://www.google.com/) with corresponding IP addresses.

Here&#39;s a cool video from Code.org explaining how the DNS works:
<iframe width="560" height="315" src="https://www.youtube.com/embed/MwxMsaFFycg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Transport Layer

## TCP &amp; UDP

The Transport layer receives the data from the layer above: Application layer.

### Purpose

The protocols of this layer are designed to:

- Facilitate the communication between applications on different hosts.
- Multiplexing – transmission of multiple signals over the shared channel – and demultiplexing.
  - Multiplexing at the Transport layer is implemented through the use of _network ports_.

#### Network ports

Network ports are the identifiers of a specific process on your machine. That is, when you want to have a music playing on the background using YouTube Music in the Chrome browser and send the email from the Outlook, network ports for Chrome and Outlook are used for enabling the multiplexing.

### Protocols governing the Transport Layer

There are two common protocols at the transport layer:

- TCP
- UDP

The implementation and the exact structure of PDUs for TCP and UDP would be different but they both would have source and destination network port numbers included in their headers.

### Transmission Control Protocol (TCP)

TCP key features:

1. Provides multiplexing capability implemented via network ports
2. Provides reliable data transfer implemented via Three-way handshake
3. Provides Flow Control
4. Provides Congestion Avoidance mechanism

TCP disadvantages:

1. Latency overhead in establishing a TCP connection due to the Three-way handshake process
2. Head-of-line blocking due to the re-transmission of the missing segments.

TCP PDUs are called Segments. **The Header** of a TCP segment consists of the source port, destination port and other TCP segment header fields. **The Segment Payload** consists of the data received from the Application layer above.

TCP is connection-oriented protocol. That means that the transfer of data does not start until the connection between application processes on the hosts is established. This process of establishing a reliable connection between applications is known as a **Three-way Handshake** :

1. The sender application sends a TCP Segment with SYN flag set to 1
2. Receiver receives SYN Segment, responds with SYN ACK Segment to the original sender.
3. Once received, original Sender responds with ACK Segment to finally establish a connection

![tcp-three-way-handshake](/assets/images/tcp-three-way-handshake.png)

#### Flow Control

Flow control is a mechanism to prevent the sender from overwhelming the receiver with too much data at once. The receiver will only be able to process a certain amount of data in a particular _timeframe_. Data awaiting processing is stored in a &#39;buffer&#39;. The buffer size will depend on the amount of memory allocated according to the configuration of the OS and the physical resources available (Transmission Control Protocol (TCP), 2020).

#### Congestion Avoidance

Network Congestion is the situation when there is more data being transmitted than there is network capacity to process and transmit the data.

TCP uses data loss as a feedback mechanism to detect and avoid network congestion  (Transmission Control Protocol (TCP), 2020).

### UDP

Another common protocol used at the Transport Layer is User Datagram Protocol (UDP). In general, UDP is way simpler protocol that TCP.

UDP key features:

1. Provides multiplexing capability implemented via network ports

UDP disadvantages:

1. No guarantee of message delivery
2. No guarantee of message delivery order
3. No built-in congestion-avoidance or flow-control mechanisms.
4. No connection-state tracking.

![arena-of-valor-mobile-game](/assets/images/arena-of-valor.png)

UDP is usually used for the networking applications that require faster connection over the more stable connection: video chat apps, mobile games.

# The Application Layer

The application layer consists of the protocols which ensure communication between applications. It does not include applications themselves. Application layer protocols focus on the structure of the message that is being sent and the data that it should contain, instead transporting of the message from point A to point B.

### Purpose

The protocols of this layer are designed to:

- Structuring the data being transferred from one application to another.

### Protocols governing the Application Layer

There are several common protocols at the application layer:

- HTTP – [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol), used for World Wide Web applications communication
- FTP – [File Transfer Protocol](https://en.wikipedia.org/wiki/File_Transfer_Protocol), used for transferring the computer files between client and server on a computer network
- [Simple Mail Transfer Protocol](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol) (SMTP) along with [Post Office Protocol](https://en.wikipedia.org/wiki/Post_Office_Protocol) (POP) or [Internet Message Access Protocol](https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol) (IMAP) – used for email transmission

### World Wide Web

World Wide Web, or simply web, is one of the services that are available on the Internet. It&#39;s not the Internet itself. Basically, web is a huge information system that consists of resources which are navigable by means of Uniform Resource Locator (URL). HTTP is the primary means by which applications interact with the resources which make up the web (HTTP and the Web, 2020).

### How does the Web work?

The high-level process is somewhat similar to the diagram below.

![ewb-diagram](/assets/images/web-diagram.png)

Here are some clarifications for the terms used in the diagram above:

- **Client** is the application you use to communicate with the server. Most commonly used client application would be a web-browser (e.g. Chrome, Mozilla Firefox, etc.). However, you can think of the game that requires constant connection to the internet as a client as well.
- **Server** is the networking device that stores the content you are trying to access from the client.
- **Resource** is the general term for things you are trying to interact with via a URL on the Internet. Videos, music, HTML, CSS, image files are all considered to be resources.
- Light blue line is used to show the HTTP request generated from the client.
- Green light is used to showcase the HTTP response which is sent back from the server

## URLs

Uniform Resource Locator (URL) is like a mobile number you need to type in in your cellphone to reach out to your friend. Also, just like a number, URL is comprised of the different parts.

Here&#39;s a diagram of what a standard URL is comprised of:

- The **Scheme** tells the client how to access the resource specified in the URL.
- The **Host** tells the client where the resource is located
- The **Port** or **Port Number** is the optional. _The default port number of the HTTP requests is_ 80_._
- The **Path** shows what local resource is being requested exactly. This part of the URL is optional.
- The **Query String** which is made up of the **Query Parameters** is used to send data to the server.

![ewb-diagram](/assets/images/url.png)

### URL Query Strings and Encoding

Query strings can be used to pass additional information to the server; however, they have some limitations:

- They have a maximum length
- The name/value pairs in the query strings are visible in the URL.
- Space and special characters cannot be used in the query string.

#### URL Encoding

Some characters are not supported by the URLs. That is, to represent them we need to use % character followed by two hexadecimal digits that represent a character needed. Here&#39;re the popular encoded characters and the example URLs:

| Character | ASCII code | URL |
| --- | --- | --- |
| Space | 20 | https://www.google.com/search?q=tommy%20hilfiger |
| ! | 21 | https://www.google.com/search?q=more%20jobs%21 |
| + | 2b | https://www.google.com/search?q=1%2b2 |
| # | 23 | https://www.google.com/search?q=%23covid |

## HTTP and the Request/Response Cycle

Application layer communication is mainly governed by the [Hypertext Transfer Protocol](https://developer.mozilla.org/en-US/docs/Web/HTTP#:~:text=Hypertext%20Transfer%20Protocol%20(HTTP)%20is,be%20used%20for%20other%20purposes.) (HTTP). The HTTP is the foundation of any data exchange on the Web.

There are two main processes that happen as per the HTTP protocol: request and response.

When you type in a URL into your browser&#39;s search bar and hit &quot;Enter&quot;, what you really do it sending the message from client that is called a **request** for information stored at that URL.

It usually takes up to 10.3 seconds to _fully_ load the webpage (Monaghan, 2020). That sounds like too long. Usually the time it takes to see the content on the webpage is way shorter, something like 2 seconds. That is because client is sending multiple HTTP requests one after another for each file that is needed to display the webpage correctly: HTML, CSS, JavaScript, image file, video file, etc. You receive a message back from the hosting server, which is called a **response** , for each of those requests. As soon as the response is received by the client, it is displayed.

![http-request](/assets/images/HTTPRequest.png)

### HTTP Request

So, what&#39;s exactly the HTTP Request? How the message to the server looks like?

An example of the HTTP Request looks like this (An overview of HTTP, 2019):

![http-request-methods](/assets/images/http-request-methods.png)

#### HTTP Request Methods

An HTTP request method is a verb, such as GET or POST that defines the operation that the client wants to perform.

Usually, we either want to receive the information from the server (using GET) or post some value to the server (using POST), so let&#39;s look into these two methods a bit more in detail.

- GET requests are used to fetch some data from the resource; most links are GETs.
- The response data from the resource can be anything; however, if it is an HTML document that references other resources, your browser (client) will request other linked resources automatically

HTTP POST method sends data to the server. A POST request is usually sent via an HTML form and results in a change on the server. The data that is sent to the server via the POST method request is contained within the HTTP **body**.

### HTTP Response

The first component of the HTTP Response is the **Status Code**. It specifies the status of the request and consists of the status code, a three-digit number, and a status text – a short description of the code.

| Status Code | Status Text | Meaning |
| --- | --- | --- |
| 200 | OK | The request is handled successfully |
| 302 | Found | The request resource has changed. Usually results in a redirect to another URL |
| 404 | Not Found | The request resource cannot be found |
| 500 | Internal Server Error | The server has encountered an error |

The most important parts of the HTTP response are:

- status code
- headers
- message body, which contains the raw response data.

## HTTP is Stateless, not Sessionless

I won&#39;t be able to say it better and more succinct than Mozilla Developer Network (An overview of HTTP, 2019):

<blockquote>HTTP is stateless: there is no link between two requests being successively carried out on the same connection. This immediately has the prospect of being problematic for users attempting to interact with certain pages coherently, for example, using e-commerce shopping baskets. But while the core of HTTP itself is stateless, HTTP cookies allow the use of stateful sessions. Using header extensibility, HTTP Cookies are added to the workflow, allowing session creation on each HTTP request to share the same context, or the same state.</blockquote>



The **state** in the context of the web is _how are_ the conditions of web application; its configuration, attributes, condition or information content (State in Web application design, 2006).

The **statefullness** of the web applications is achieved through the use of the following technologies:

1. **Sessions**. Whenever client makes a request to the server, it appends a session identifier as part of the request. This allows the server to identify the clients.
2. **Cookies**. When you access given website for the first time, the server sends session information and sets it in your browser cookie – small file that contains the session id – on your local machine.
3. **AJAX** / Asynchronous JavaScript and XML – allows client to make requests to the server and process the responses without a full-page refresh.

# Security

HTTP protocol does not provide the secure application to application communication by itself. There are some risks that a hacker would somehow get cookies from your browser and then retrieve session id token. This would allow a hacker to design an HTTP request that includes a session id and let her/him sign into the application without login details.

## Secure HTTP (HTTPS)

With HTTPS every response or request on the network is encrypted and would be useless to the hackers. HTTPS is using [TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security), a cryptographic protocol, that is designed to encrypt messages send from client to server and vice versa.

## Same Origin Policy

This is the concept that allows unrestricted access to between the resources of the same origin and restricts certain interactions between resources from different origins.

The **origin** is the combination of URL&#39;s scheme, hostname and port.

![url-same-origin](/assets/images/url-same-origin.png)

### Session Hijacking

The situation in which hacker gets hold of the session id. In this case s/he can access the web application without password or username.

Common ways to fight session hijacking are:

- **Resetting sessions** for sensitive places in the account. That is why changing passwords or accessing the financial data would usually require you to provide your username and passcode once again.
- Setting an **expiration time for a session**.
- **Using HTTPS across the entire app** to minimize the chances of getting the session id.

### Cross-Site Scripting

This type of cyber-attack might happen if you allow the users to input HTML or JavaScript that ends up being displayed on the website.

For example, if you have the form on the website that allows to input the HTML/JS directly, hackers input might be executed by the browser. With this technic attacker can fetch the session id of the future visitors of the website and then use it to their advantage.

Here are solutions to this security issue :

- Sanitize every input by eliminating problematic input, such as \&lt;script\&gt; tags or disallowing HTML and JavaScript input altogether.
- Escape all user input data when displaying it so that the browser does not interpret is as a code.

## The Transport Layer Security (TLS) Protocol

HTTP protocol does not secure the message it transfers from one point in the network to another. That is why to make sure nobody is sneaking on some potentially sensitive information, the **Transport Layer Security (TLS)** protocol is implemented.

TLS key services (The Transport Layer Security (TLS) Protocol, n.d.):

1. **Encryption** – a process of encoding a message so that it can only be ready by those with authorized means of decoding the message
2. **Authentication** – a process to verify the identity of a particular party in the message exchange
3. **Integrity** – a process to detect whether a message has been interfered with or faked in any way

### TLS Encryption

TLS sets up the secured encrypted connection by using the process called TLS Handshake.

To further understand how the modern encryption work, we have to understand what the **Symmetric Key Encryption** is. As per this encryption system, both sender and receiver should have access to the same encryption key and no one else.

This possess a problem of sharing this key between the sender and the receiver and leads to the use of the **Asymmetric Key Encryption** (aka public key encryption). Unlike in the symmetric system, in the asymmetric one the keys in the pair are not the same: the public key is used to encrypt the message and _only_ the private key to decrypt it.

TLS uses a combination of the symmetric and asymmetric cryptography. The biggest part of the message exchange uses the symmetric key encryption; however, the initial symmetric key exchange is conducted using asymmetric key encryption. The process by which the initial secure connection (asymmetric encryption) is created is conducted during the process known as **TLS handshake**.

TLS assumes that TCP is used at the Transport Layer, and TLS handshake takes place after the TCP handshake. The TLS handshake process at the high level looks like this:

1. The TLS handshake begins with a ClientHello message which is sent immediately after the TCP ACK. This message contains the maximum version of the TLS protocol that the client can support, and a list of Cipher Suites that the client can use.

<blockquote>Cipher suite is the combination of algorithms that are used for the key exchange process, authentication, symmetric key encryption and checking message integrity (TLS Encryption, n.d.).</blockquote>

1. The server responds to the ClientHello message. This message consists of the ServerHello, which sets the protocol version and the Cipher Suite and some related data. As part of this message the server also sends its certificate (which contains a public key), and a ServerHelloDone marker which indicates to the client that it has finished this step of the handshake.
2. The client receives the ServerHelloDone marker and initiates the symmetric key exchange process. Algorithms of the symmetric key exchange may vary, but you can check how the [RSA cryptosystem](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) works to get the idea.
3. In the end, the server sends a message with ChangeCipherSpec and Finished flags. The client and server can now begin secure communication using the symmetric key.

Here&#39;s a simple diagram to visually represent the process:

![tls-handshake](/assets/images/tls-handshake.png)

**It&#39;s important to remember following about the TLS handshake:**

- It&#39;s used to agree which version of the TLS to be used in establishing a connection
- It&#39;s used to agree on the algorithms that will be in the cipher suite
- It allows the exchange of the symmetric keys that will be used for the message encryption.

Also, while secure, TLS has an impact on performance on top of the TCP.

### TLS Authentication

The Authentication process looks something like this:

- The Server sends its certificate that includes the _public key_
- The Server creates a signature in the form of encrypted data with the server&#39;s _private_ key
- The Signature is transmitted in a message along with the original data from which the signature was created
- On receipt of the message, the client decrypts the signature using the server&#39;s public key and compares the decrypted data to the original version.
- If the two versions match, then the encrypted version could only have been created by a party in possession of the private key.

### TLS Integrity

Just like any other PDU, TLS encapsulates data in a form of payload and header &amp; trailer that contain the meta data.

The main field of interest in terms of message integrity is the MAC (_Message Authentication Code_) field.

The Message Authentication Code is a field that concerns itself to providing a means of checking that the message has not been altered with in the transit. This is implemented through the use of the hashing algorithm. The hashing algorithm that is used in specific is agreed upon in the Cipher Suite approved during the TLS handshake.

# Works Cited

Center, P. R. (2014, November). _What Internet Users Know About Technology and the Web._ Retrieved from [https://www.pewresearch.org/internet/wp-content/uploads/sites/9/2014/11/PI\_Web-IQ\_112514\_PDF.pdf](https://www.pewresearch.org/internet/2014/11/25/web-iq/)

_Protocols_. (2020, October). Retrieved from launchschool.com: [https://launchschool.com/lessons/4af196b9/assignments/a53e65ce](https://launchschool.com/lessons/4af196b9/assignments/a53e65ce)

_HTTP and the Web_. (2020, November 2). Retrieved from launchschool.com: [https://launchschool.com/lessons/cc97deb5/assignments/e3d85587](https://launchschool.com/lessons/cc97deb5/assignments/e3d85587)

_Transmission Control Protocol (TCP)_. (2020, November 1). Retrieved from launchschool.com: [https://launchschool.com/lessons/2a6c7439/assignments/d09ddd52](https://launchschool.com/lessons/2a6c7439/assignments/d09ddd52)

Monaghan, M. (2020, August 19). _Website Load Time Statistics: Why Speed Matters in 2020_. Retrieved from www.websitebuilderexpert.com: [https://www.websitebuilderexpert.com/building-websites/website-load-time-statistics/](https://www.websitebuilderexpert.com/building-websites/website-load-time-statistics/)

_An overview of HTTP_. (2019, 09 29). Retrieved from developer.mozilla.org: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

_State in Web application design_. (2006, 04 19). Retrieved from www.w3.org: [https://www.w3.org/2001/tag/doc/state.html#whatisstate](https://www.w3.org/2001/tag/doc/state.html#whatisstate)

_The Transport Layer Security (TLS) Protocol_. (n.d.). Retrieved from launchschool.com: [https://launchschool.com/lessons/74f1325b/assignments/83bf156b](https://launchschool.com/lessons/74f1325b/assignments/83bf156b)

_TLS Encryption_. (n.d.). Retrieved from launchschool.com: [https://launchschool.com/lessons/74f1325b/assignments/54f6defc](https://launchschool.com/lessons/74f1325b/assignments/54f6defc)