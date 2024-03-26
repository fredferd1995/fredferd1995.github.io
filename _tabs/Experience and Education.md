---
# the default layout is 'page'
title: Experience and Education
icon: fas fa-info-circle
order: 1
---

I've been writing software professionally since 2018.

> [Current Resume]({{ site.baseurl }}{% link /assets/files/fhresume2024.pdf %})
{: .prompt-tip}

## Experience
#### AppStem
*Software Development Engineer*
- Develop RESTful APIs (TypeScript), docs (Swagger) and data models (PostgreSQL) to support user authentication, media uploads, posts, and interactions for a greenfield Node.js-based social media app
- Identified and mitigated error-handling risks in legacy codebase by refactoring critical database operations into atomic transactions, ensuring data consistency and system reliability


#### Amazon Web Services (AWS) - [OpsCenter](https://docs.aws.amazon.com/systems-manager/latest/userguide/OpsCenter.html)
*Software Development Engineer*
    
- Empowered OpsCenter customers (56K active WoW) to increase security posture by designing/coding attribute‑based access control service.
    - Integrated with AWS Identity service, allowing customers to scope resource access based on resource metadata.
    - __End Result__: Customers are able to scope access to operational items based on "context keys".
- Migrated 13 internal/external APIs from manual to automated __python__/__boto3__ security testing framework, bringing coverage to 100%.
    - __End Result__: Improved team development velocity from months to weeks by leveraging this immediate automated security coverage.
- Implemented custom alarms, metrics, logging, and dashboards to monitor new feature adoption and health. 
    - __End Result__: Logging and runbook additions helped bring on‑call MTTR down to minutes from hours, saving time, money and customer impact.
- Wrote code, tests on 4 dev team for design, implementation of feature to support cross‑account resource access.
    - __End Result__: Reduced latency on calls to AWS Organizations API, saving up to 12s in some cases.
- Authored design documents and drove team consensus on new feature design and implementation.



#### Lockheed Martin, Santa Barbara Focalplane
*Infrared Imaging Systems Engineer*

- Technical Lead on largest infrared camera contract for site. Regularly worked with partner teams and customers in multiple US locations.
- Led technical projects, 4 technicians, 2 test engineers. Managed budget. Researched, documented, communicated technical details, and defended proposals, analysis to site leadership.
- Implemented simulation of upstream image‑processing suite, extensible to different types of imagery data. Software enabled validation/introduction of new detector design.
    - __End Result__: Obsoleted need for additional in‑flight testing and validation, saving months of planning and thousands of dollars.
- Performed statistical analysis on infrared camera data (MATLAB, Python), which informed process changes, reduced failure modes, improved yield.
    - __End Result__: Cases include complete reduction of infant mortality failure mode, and improvements in detector yield by up to 50% in some runs.
- Developed, released production software to test camera systems and measure performance against requirements.


## Projects, Academic and Personal

#### CPU Scheduler/Memory Coordinator for Virtual Machines
*C, Linux, Libvirt, Azure*

- Balance VCPU utilization across a set of physical CPUs on a cloud-based Azure instance running 8 virtual machines. Use a greedy knapsack-based pinning scheme to balance utilization across physical cores
- Use memory ballooning techniques to determine when to provision/reclaim memory to and from host

#### Multi‑threaded Distributed File System
*C++14 w/ STL, gRPC, Docker, Linux, WSL2*

- Distributed multi‑threaded file server/storage (think ”minimal Dropbox”) in C++, which will list, upload, download, and delete a consensus of
shared files across multiple clients (threads).

- Utilized gRPC to communicate actions across clients/server.

- Implemented mutexes/other synchronization constructs for thread safety.

#### Cache‑Based File Server
*C, POSIX, Linux*
- Multi‑threaded file server. Files are sent to client from a local cache of frequently‑requested files in order to reduce client wait time.
- Cache reads are performed via synchronous access to shared memory segments via the POSIX API and semaphores

#### Classification‑Based Learner for Stock Trading GATech
*Python, Pandas, NumPy, Linux*
- Stock bot that advises buy/sell/short decisions. Trained via Classification‑Based Decision Tree learner on an input data set of historical
price/volume data. Yielded positive returns after training period

## Education
#### Georgia Institute of Technology
M.S. Computer Science, emph. Computing Systems (Expected 2024)
    
    - Computer Architecture
    - Artificial Intelligence
    - Information Security
    - Software Architecture and Design
    - Machine Learning for Trading
    - Game Artificial Intelligence
    - Computer Networks
    - Advanced Operating Systems
    - Graduate Algorithms

#### University of California, Santa Barbara
B.S. Physics
    
    - Analog, Digital Electronics
    - Quantum Mechanics
    - Statistical Mechanics/Thermodynamics
    - Particle Physics
    - Advanced Mechanics
    - Complex Analysis
    - Electromagnetism
