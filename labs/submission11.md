# Lab 11 submission

## Task 1

![10.1](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab11/labs/assets/screenshots/lab10.1.png?raw=true)
![10.3](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab11/labs/assets/screenshots/lab10.3.png?raw=true)

**Test file CID:** QmeCk4kWvyBs8qVDzrHTd43aRnaS2uB37HVyUwUMSSgrSY

![10.2](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab11/labs/assets/screenshots/lab10.2.png?raw=true)

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

## Task 2

**4EVERLAND project URL:** devops-intro-t8f1ppiu-sarrtr.ipfs.4everland.app

**IPFS CID from 4EVERLAND dashboard:** bafybeigebxk655ctkbicst3phebdohknivtortqm4j66sv42rypolfcnd4

**4EVERLAND deployment dashboard:**

![10.4](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab11/labs/assets/screenshots/lab10.4.png?raw=true)

**Site accessed through 4EVERLAND domain:**

![10.5](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab11/labs/assets/screenshots/lab10.5.png?raw=true)

**Site accessed through public IPFS gateway:**

![10.6](https://github.com/sarrtr/DevOps-Intro/blob/feature/lab11/labs/assets/screenshots/lab10.6.png?raw=true)

**Analysis: How does 4EVERLAND simplify IPFS deployment compared to manual methods?**

With manual IPFS deployment we need to:
- Install and configure an IPFS node
- Add and pin files yourself
- Manage gateways for public access
- Handle updates (which generate new content hashes)
- Ensure persistence by using pinning services

4EVERLAND provides:
- One-click deployment similar to platforms like traditional web hosting services
- Automatic file uploading and pinning, so content remains available
- Integrated gateways and CDN acceleration, making content faster to access
- Versioning and continuous deployment (CI/CD), allowing developers to redeploy updates easily
- User-friendly dashboards, removing the need for command-line interaction

**Comparison: What are the trade-offs between traditional web hosting and IPFS hosting?**

Traditional Web Hosting:

Pros:
- Reliable performance: Fast and predictable due to dedicated infrastructure
- Easy updates: Files can be modified without changing URLs
- Mature ecosystem: Extensive tools, support, and integrations
- Better control: Full authority over data, access, and deletion

Cons:
- Single point of failure: Server outages can make sites inaccessible
- Censorship risk: Content can be taken down by providers or authorities
- Security risks: Centralized targets are more vulnerable to attacks

IPFS Hosting:

Pros:
- High resilience: Content is distributed across many nodes
- Content integrity: Files are verified via hashes (tamper-proof)
- Censorship resistance: Harder to remove content globally
- Efficient distribution: Popular content can be served from multiple peers

Cons:
- Update friction: Any change creates a new content hash (new address)
- Availability challenges: Content must be pinned or hosted to persist
- Performance inconsistency: Depends on peer availability and network conditions
- Learning curve: More complex than traditional hosting