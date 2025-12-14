#### Why network?

---

Imagine you have a huge task that needs a whole crew. You could all crowd around a single computer, but it would be slow and confusing. Or, each member could have their own computer, connected by a network, allowing everyone to work simultaneously and share files or updates instantly as part of the same project.
cutting to the chase why do we need it-

* to overcome geographical separations.
* resource sharing.
* scalability and flexibility.
* centralized data access and storage.



###### What is the Internet?

The Internet (short for Inter-network) is a vast, global network that connects millions of computers around the world, enabling them to communicate and share information.

###### 

###### How Are Computers Connected Globally?

It’s neither feasible nor practical to lay millions of cables directly connecting every single computer worldwide. Instead, the internet relies on devices called routers to direct data traffic efficiently across networks.

###### 

###### Role of Routers in the Internet

Routers act as intermediaries that guide data packets along optimal paths to reach the correct destination. Rather than requiring direct connections between every device, routers facilitate communication by forwarding data between interconnected networks.

###### 

###### Why Routers Are Essential:

###### 

They eliminate the need for direct wiring between every device, making large-scale connectivity possible.



They dynamically determine the best path for data to travel, optimizing network traffic.



They provide security features such as firewalls and manage IP address allocation through protocols like DHCP.



Without routers, the internet as a scalable and resilient global network would not exist.



##### Moving Forward: The OSI Model

As we dive deeper into networking, it’s important to understand the fundamental framework that helps us organize and understand how data travels across these networks—the OSI (Open Systems Interconnection) Model. This model breaks down network communication into seven layers, each with a specific role, providing a universal reference for designing, troubleshooting, and teaching networking concepts.







#### The OSI (Open Systems Interconnection) Model



the OSI model is a theoretical framework that defines how network communication should occur across seven distinct layers. It’s widely used for educational and conceptual purposes, helping professionals understand and troubleshoot networking systems.



*Need*:

---

to put it simply in my words, assume we run a package delivering services... now there is a set of rules our customers needs to follow, Think of networking like running a parcel delivery service. To guarantee safe delivery, customers must follow a set of standardized rules—like proper packaging and addressing. Reference models in networking serve the same purpose: they define clear procedures so data can travel securely and efficiently across devices



Brief Description of Each Layer



***The Bottom Layers:-***



1. ###### Physical Layer:

---

Transmits raw binary data (bits) over physical media. Deals with cables, switches, electrical signals, radio waves, and hardware specifications.



###### 2\. Data Link Layer:

Packages bits into frames, handles error detection/correction on the physical link, and manages MAC addresses to identify devices on the same network segment.



###### 3\. Network Layer:

Routes packets between different networks using logical addresses (IP addresses). Responsible for packet forwarding, routing, and traffic control.



###### 4\. Transport Layer:

Ensures complete data transfer with mechanisms for error checking, flow control, and data segmentation. Protocols like TCP guarantee ordered and lossless delivery; UDP is faster but connectionless.



***The Upper Layers:-***



5. ###### Session Layer:

---

Manages sessions or connections between two computers—establishes, maintains, and terminates communication.



###### 6\. Presentation Layer:

Translates data formats between the application and the network (e.g., encoding, encryption, compression).



###### 7\. Application Layer:

Closest to the user; interfaces with software applications to provide network services like web browsing (HTTP), file transfer (FTP), email (SMTP), and more.

Each layer adds or processes specific information — such as formatting, error correction, addressing, routing, and converting to electrical signals — to prepare the data for transmission over the physical network.





***Mnemonics for OSI Layers- "Please Do Not Throw Sausage Pizza Away"* or (receiver's POV)**

**<i>                          "All People Seem To Need Data Processing"   </i>(sender's POV)**





**Let’s say you’re loading a website on your browser:**



You type www.example.com and hit enter (**Application Layer**).



Your computer asks for the right “language” (HTML, images, etc.) and encrypts your login details (**Presentation Layer**).



It establishes a connection to the server (“session”), so the data can be exchanged (**Session Layer**).



Your browser breaks the data into packets (**Transport Layer**). If any packet doesn’t arrive, it’ll ask for a resend.



Each packet gets an address (IP) and is routed across the globe’s internet backbone (**Network Layer**).



On your local Wi-Fi, your laptop’s data sits in a “frame” using your router’s MAC address (**Data Link Layer**).



The information is ultimately sent as electrical signals through your Ethernet cable or as radio waves with Wi-Fi (**Physical Layer**).



the other recognized model is of "***DoD (Department of Defense)" which is the foundation of the internet we know it as TCP/IP.***





#### What is TCP/IP protocol suite?

