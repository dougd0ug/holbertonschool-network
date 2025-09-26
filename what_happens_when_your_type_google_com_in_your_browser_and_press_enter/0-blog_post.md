# What Happens When You Type https://www.google.com and Press Enter

When you hit Enter in your browser, a complex chain of events begins. Let’s break it down step by step:

## 1. DNS Request

Your browser first checks its cache (or the OS cache) for the IP of www.google.com.
- If not found, it asks the DNS resolver (usually your ISP or Google DNS 8.8.8.8).
- The resolver queries the root DNS servers, then the .com TLD servers, and finally Google’s authoritative DNS servers.
- You get back an IP address (like 142.250.190.4).

## 2. TCP/IP Connection

- Using the IP, your computer opens a TCP connection with Google’s servers over port 443 (HTTPS).
- TCP ensures reliable delivery (3-way handshake: SYN, SYN-ACK, ACK).
- The data is wrapped in IP packets to travel across the internet.

## 3. Firewall

- Both your computer and Google’s servers may have firewalls filtering packets.
- Only traffic on allowed ports (like 443 for HTTPS) gets through.

## 4. HTTPS / SSL

- Your browser and Google’s server negotiate a TLS handshake.
- The server presents its SSL certificate, signed by a trusted Certificate Authority (CA).
- If valid, an encrypted session key is exchanged.

From now on, all traffic is encrypted.

## 5. Load Balancer

- Google uses global load balancers to distribute requests across many servers.
- The load balancer decides where to route your request, often using algorithms like round-robin or least connections.

## 6. Web Server

- The request hits a web server (like Nginx or Apache).
- The web server handles static content (images, CSS, JavaScript) and forwards dynamic requests to the application server.

## 7. Application Server

- The application server (Google’s backend) processes your search query.
- It applies business logic, queries other services, and prepares a response (HTML, JSON, etc.).

## 8. Database

If needed, the app server queries a database.
- Databases store structured information (like indexed search results).
- The result is returned to the application server, then to the web server, and finally back to your browser.

## 9. Rendering in Browser

Your browser receives the HTML response.

It parses the DOM, loads CSS and JavaScript, and renders the Google homepage.
