# Lab 11 submission

## Task 1

![10.1]()
![10.3]()

**Test file CID:** QmeCk4kWvyBs8qVDzrHTd43aRnaS2uB37HVyUwUMSSgrSY

![10.2]()

**Analysis: How does IPFS's content addressing differ from traditional URLs?**

IPFS uses content addressing, which is different from traditional URL-based addressing. In traditional web systems (HTTP/HTTPS), a URL points to a location (e.g., a specific server like example.com/file.txt). If the server goes down or the file is moved, the link breaks. In IPFS, content is addressed by a cryptographic hash of the file itself (called a CID – Content Identifier). 

This means:
- The address is derived from the file’s content, not its location.
- If the content changes, the hash (and therefore the address) also changes.
- Files can be retrieved from any node that has a copy, not just one server.

**Reflection: What are the advantages and disadvantages of decentralized storage?**

Advantages of decentralized storage:
- Resilience: No single point of failure—data can still be accessed even if some nodes go offline.
- Censorship resistance: Harder for governments or organizations to remove or block content.
- Data integrity: Content addressing ensures files haven’t been altered (hash verification).
- Efficiency: Popular content can be cached across many nodes, improving download speeds.

Disadvantages of decentralized storage:
- Availability uncertainty: Content may become inaccessible if no nodes are hosting it.
- Performance variability: Retrieval speed can depend on network conditions and peer availability.
- Complexity: Harder to manage, debug, and maintain compared to centralized systems.
- Storage incentives: Without proper incentive mechanisms, nodes may not keep hosting data.
- Privacy concerns: Data distributed across many nodes may be harder to control or delete.

## Task 1