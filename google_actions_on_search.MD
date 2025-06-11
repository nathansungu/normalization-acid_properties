# WHAT HAPPENS WHEN YOU SEARCH ON GOOGLE

## DNS RESOLUTION:<br>
The first step is your web browser sends a request to a DNS (Domain Name System) server to resolve the URL (Uniform Resource Locator) into an IP address. The DNS server looks up the IP address associated with the URL and returns it to the browser.<br>
- Why Use DNS<br>
Its easier to remember a word like jumia.com reather than a long number such as 172.217.3.111.<br>
- How DNS Works<br>
Your computer starts by asking your local DNS server. If it doesn’t know, it asks other servers until it finds the answer. This process happens incredibly fast.<br>
    
They are <b> 4 DNS Servers</b><br>

1. <b>Local DNS Resolver</b>: <br>This is your computer or network’s DNS resolver. It’s the first point of contact when you try to access a website. It checks its cache for the IP address associated with the domain name you’re looking up.
1. <b> Root DNS Server</b>:<br> The local DNS resolver contacts a root DNS server. These servers are at the top of the DNS hierarchy and provide information about the TLD (top-level domains) like .com, .org.
1. <b>TLD DNS Server</b>: The root DNS server directs the local resolver to the appropriate TLD DNS server. TLD servers handle requests for specific domain extensions, such as .com, .org, or .net.
1. <b> Authoritative DNS Server</b>: Directs the local resolver to the authorities DNS server for the specific domain you're trying to access.

- once the IP address is found, it is used to connect with the convinient server via TCP/IP.

## TCP/IP:<br>
### What Is TCP
Transmissio Controll Protocol - is the process by which two devices, like your computer and a web server, make a reliable connection to exchange data.<br><br>
Once the IP address is obtained, the browser initiates a TCP/IP  connection with the server that hosts the website. TCP/IP is a set of communication protocols that allow computers to communicate with each other over the internet.

### Why Establish TCP/IP
<br>Ensure that the data transmitted reaches to the correct desired destination by verifying the paties communicating.

- Esdtablishing TCP/IP Connection
<br>

 1. `Initiation:` Your computer sends a message to the server, saying, “Hey, I want to talk!” This is called a SYN (synchronize) request.

1. `Acknowledgment:` The server replies, “Sure, let’s talk.” It acknowledges your request with a SYN-ACK message.

 1. `Connection Established:` Finally, your computer sends an ACK message back to the server. Now the connection is established, and data can flow back and forth smoothly.

Once connection is established your computer and server can share information between each other to its destination intact.

## Firewall:<br>
Before any data can be transferred between the client and the server, the firewall checks the request to ensure that it is not malicious. A firewall is a security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules.<br>
- How Does Firewall Work
    1. Packet Filtering: It looks at individual packets and make decisions based on the predefined rules.
    1. Stateful Inspection:  It knows if a request from inside the network matches an expected response from outside. If it doesn’t, the firewall blocks it.
    1. Deep Packet Inspection (DPI):  PI examines the actual content of data packets, looking for signs of malware or other threats.
    


## HTTPS/SSL HandShake:
If the firewall approves the request, the web browser and the server establish a secure HTTPS (Hypertext Transfer Protocol Secure) connection using SSL (Secure Sockets Layer) or TLS (Transport Layer Security) encryption. This encryption ensures that all communication between the client and server is secure and cannot be intercepted by third parties.<br>
## Load-balancer:<br>
The load balancer is a server that distributes incoming network traffic across multiple web servers to ensure that no single server is overloaded with requests.
## Web server:<br>
It’s a computer that stores and delivers web pages and other digital content to users when they request it through a web browser.
When a user request for dynamic content the webserver process it and sends it to the application server.

## Application server:<br>
 The application server generates the dynamic content and returns it to the requested web server.
 Application servers are used to handle this complexity. They make sure that web applications, mobile apps, and other digital services run smoothly, efficiently, and securely. They are crucial for creating interactive and dynamic online experiences.

## Database:<br>
If the dynamic content requires data from a database, the application server sends a request to the database server. The database server retrieves the requested data and sends it back to the application server, which generates the dynamic content and sends it back to the web server.
![image of database visualization](https://miro.medium.com/v2/resize:fit:1100/format:webp/0*8tR6flSIhtgHlmM4)

## Web server again:
Finally, the web server sends the HTTP response, which includes the requested webpage, to the client's web browser. The web browser receives the response and displays the webpage on the user's screen.
  - this includes: <br>
    - HTML Parsing: The browser reads the HTML code of a web page.
    - CSS Styling: Once the HTML is parsed, the browser processes the CSS

    ![webpage](https://miro.medium.com/v2/resize:fit:1100/format:webp/0*QcVAxrdQYtf5J_mz)


    
### Conclusion
By following this steps: DNS ensures that the correct IP is mapped to the website or resource, where the TCI/Ip ensures the only intended parties communicate by establishing connection. Firewall filters out possible malicious packets for secure communication.

