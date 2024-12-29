# 100 - Setup

the setup process:

1. **Create Cloudflare Account**:
   - Go to cloudflare.com
   - Sign up for a free account
   - Select "Add a Site" and enter vanheemstrasystems.com

2. **Initial DNS Setup**:
   - Cloudflare will scan your existing DNS records
   - Review and keep any existing records you want to maintain
   - Add your new subdomain records:
     ```
     # Example setup in Cloudflare
     foo-management  CNAME  your-hetzner-host.com  (Proxied - Orange Cloud)
     bar-management  CNAME  your-other-host.com    (Proxied - Orange Cloud)
     ```

3. **Update Nameservers at Versio**:
   - Log into your Versio account
   - Look for DNS/Nameserver settings
   - Replace current nameservers with the ones Cloudflare provides
   - Cloudflare will give you something like:
     ```
     ns1.cloudflare.com
     ns2.cloudflare.com
     ```

4. **Verify Setup**:
   - Wait for nameserver propagation (can take up to 24 hours)
   - Cloudflare will email you when active
   - Check status in Cloudflare dashboard
   - Test your subdomains

5. **Recommended Settings in Cloudflare**:
   - SSL/TLS: Set to "Full" or "Full (Strict)"
   - Enable "Always Use HTTPS"
   - Set minimum TLS version to 1.2
   - Enable "Auto Minify" for web optimization
   - Enable "Brotli" compression

6. **Test Functionality**:
   ```bash
   # Test DNS resolution
   dig foo-management.vanheemstrasystems.com
   
   # Test HTTPS access
   curl -I https://foo-management.vanheemstrasystems.com
   ```
