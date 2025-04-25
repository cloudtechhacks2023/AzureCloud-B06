**Azure Front Door Notes**

### 1. **Introduction to Azure Front Door**
- Azure Front Door is a scalable and secure global entry point for web applications.
- It provides global load balancing, content acceleration, and security features.
- Works at the application layer (Layer 7) using HTTP/HTTPS.

### 2. **Key Features**
- **Global Load Balancing:** Routes traffic across multiple regions for high availability.
- **Application Acceleration:** Uses Microsoft's global network for fast content delivery.
- **SSL Offloading:** Offloads SSL encryption/decryption to Front Door to improve backend performance.
- **Web Application Firewall (WAF):** Protects against common web attacks.
- **URL-Based Routing:** Directs traffic based on request URLs.
- **Session Affinity:** Ensures users maintain session state with a specific backend.
- **Custom Domains & HTTPS:** Supports custom domains with automatic HTTPS.
- **Caching:** Improves performance by caching content at edge locations.

### 3. **Architecture and Components**
- **Frontend Hosts:** Represents the domain name used to access the application.
- **Routing Rules:** Defines how requests are processed and forwarded.
- **Backend Pools:** Contains the list of backend servers or services.
- **Health Probes:** Monitors the availability of backend services.
- **Rules Engine:** Provides fine-grained control over request handling.

### 4. **Use Cases**
- **Global Web Applications:** Ensures low-latency access for users worldwide.
- **Disaster Recovery & High Availability:** Routes traffic to healthy backend regions.
- **DDoS Protection & Security:** Blocks malicious traffic using WAF.
- **Multi-Region Deployments:** Balances traffic across multiple Azure regions.
- **E-Commerce & API Acceleration:** Enhances performance with caching and routing rules.

### 5. **Comparison with Other Azure Load Balancing Services**
| Feature               | Azure Front Door | Azure Traffic Manager | Azure Load Balancer | Application Gateway |
|----------------------|----------------|----------------------|------------------|-----------------|
| Layer               | 7 (Application) | DNS-Based           | 4 (Transport)   | 7 (Application) |
| Global Load Balancing | Yes            | Yes                  | No               | No              |
| Security Features    | WAF, DDoS      | No                   | No               | WAF, TLS       |
| Session Affinity    | Yes            | No                   | No               | Yes             |
| CDN Integration     | Yes            | No                   | No               | No              |

### 6. **Deployment Steps**
1. **Create an Azure Front Door instance** in the Azure Portal.
2. **Define a frontend host** (custom domain or Azure-provided domain).
3. **Create backend pools** (Azure App Service, VMs, Storage, etc.).
4. **Configure routing rules** to define request handling.
5. **Enable security features** like WAF and SSL/TLS.
6. **Monitor and test** the deployment using Azure Monitor and diagnostics.

### 7. **Best Practices**
- Use multiple backend regions for high availability.
- Enable WAF for enhanced security.
- Optimize routing rules for performance and cost.
- Regularly monitor traffic and backend health.
- Use caching to improve response times.

### 8. **Pricing Considerations**
- Pricing depends on **traffic volume, routing rules, WAF usage, and custom domain SSL certificates**.
- Costs are calculated based on **requests, data transfer, and rules processing**.
- Consider Azure CDN for static content to reduce costs.

### 9. **Limitations**
- Not suitable for non-HTTP/S traffic.
- Can have latency overhead in specific regions.
- WAF policies might need fine-tuning to prevent false positives.

### 10. **Conclusion**
- Azure Front Door is ideal for global, secure, and high-performance web applications.
- It offers advanced routing, security, and acceleration features.
- Proper configuration and best practices ensure optimized performance and cost-efficiency.

