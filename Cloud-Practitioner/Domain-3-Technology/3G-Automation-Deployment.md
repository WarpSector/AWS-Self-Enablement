# Domain 3: Technology
# (3G: Automation and Continuous Integration (CI)/Continuous Deployment (CD))

## Amazon CloudFront
  * ### Overview
    * CloudFront is a **content delivery network (CDN)** that stores (caches) content (images, videos, apps, APIs) at Edge locations across the globe.
    * CloudFront allows you to deliver your content to users around the world faster and with low latency while also protected against DDoS attacks (Amazon Shield comes standard for DDoS protection and attaching a WAF also helps block XSS/SQL injection attacks).

## AWS Global Accelerator (same notes from the *3D Networking Markdown*)
 * ### Overview
   * Global Accelerator improves the availability and performance of applications for local and global users.
   * Global Accelerator uses the AWS Global Network to optimize the path for users to applications, which improves the performance of TCP and UDP traffic (such a online gaming).
   * Example: Users accessing applications via TCP/UDP traffic --> Routed to Regional Edge Location --> Global Accelerator uses the AWS Global Network backbone to optimize traffic to Origin Regions.
   * Global Accelerator accomplishes this by providing static IP addresses (anycast IPs) that act as fixed entry points to application endpoints in a single and/or multiple Regions (connecting to ALBs, NLBs, or EC2 instances).

