# 200 - Diagrams

A diagram showing the DNS and routing flow for your setup using Mermaid.​​​​​​​​​​​​​​​​

```mermaid
flowchart LR
    subgraph Internet
        Browser["User's Browser"]
    end

    subgraph "Domain Registration"
        Versio["Versio\n(Domain Registrar)"]
    end

    subgraph "DNS Management"
        Cloudflare["Cloudflare\n(DNS & Proxy)"]
    end

    subgraph "Web Hosting"
        Valyent["Valyent\n(Web Application Host)"]
    end

    %% DNS Setup Flow
    Versio -->|"Delegates DNS via\nNameservers"| Cloudflare
    
    %% Request Flow
    Browser -->|"1 Requests\nprompt-management.\nvanheemstrasystems.com"| Cloudflare
    Cloudflare -->|"2 Routes request to\nValyent application"| Valyent
    Valyent -->|"3 Returns web\napplication content"| Cloudflare
    Cloudflare -->|"4 Delivers content\nwith added security\nand optimization"| Browser

    %% Styling
    classDef provider fill:#f9f,stroke:#333,stroke-width:2px
    classDef service fill:#bbf,stroke:#333,stroke-width:2px
    class Versio,Cloudflare,Valyent provider
    class Browser service
```

Let me explain the key components and flow:

1. **Domain Registration (Versio)**:
   - Maintains the domain registration for vanheemstrasystems.com
   - Delegates DNS authority to Cloudflare via nameserver settings

2. **DNS & Proxy (Cloudflare)**:
   - Manages DNS records including the prompt-management subdomain
   - Provides security, caching, and optimization
   - Routes traffic to Valyent
   - Acts as the "broker" in your setup

3. **Web Host (Valyent)**:
   - Hosts the actual web application
   - Receives traffic via Cloudflare's proxy

4. **Request Flow**:
   - User requests prompt-management.vanheemstrasystems.com
   - Request goes through Cloudflare's global network
   - Cloudflare forwards to Valyent
   - Response returns through Cloudflare to user

This setup gives you:
- Centralized DNS management
- Easy host changes if needed
- Added security and performance from Cloudflare
- Clean separation of concerns between registration, DNS, and hosting

