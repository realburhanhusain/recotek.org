# Domain Redirect Configuration for Recotek.org

This document explains how to set up domain redirects so that all alternate domains redirect to the main domain `recotek.org`.

## Domains to Redirect

The following domains should redirect to `https://recotek.org`:
- recotek.in
- recotek.shop
- recotek.online
- recotek.store

## Setup Instructions

### Method 1: DNS-Level Redirects (Recommended)

Configure your DNS provider to set up URL forwarding/redirects:

1. **For each alternate domain** (recotek.in, recotek.shop, recotek.online, recotek.store):
   - Log in to your domain registrar/DNS provider
   - Look for "URL Forwarding", "Domain Forwarding", or "Redirect" settings
   - Set up a 301 permanent redirect from the alternate domain to `https://recotek.org`
   - Enable "Forward with masking" if you want the URL to change in the browser
   - Enable HTTPS/SSL for secure redirects

2. **Example configurations**:

   **GoDaddy:**
   - Go to Domain Settings → Forwarding
   - Add Forward to Domain: `https://recotek.org`
   - Forward Type: Permanent (301)
   - Update Forwarding

   **Namecheap:**
   - Go to Advanced DNS → Domain Redirect
   - Type: Permanent Redirect (301)
   - Source URL: @ (root domain)
   - Destination URL: `https://recotek.org`

   **Cloudflare:**
   - Use Page Rules to create redirects
   - URL: `*recotek.in/*`
   - Setting: Forwarding URL (301 - Permanent Redirect)
   - Destination: `https://recotek.org/$1`

### Method 2: Web Server Redirects

If you have web hosting for the alternate domains, configure server-level redirects:

#### Apache (.htaccess)
```apache
RewriteEngine On
RewriteCond %{HTTP_HOST} ^(www\.)?recotek\.(in|shop|online|store)$ [NC]
RewriteRule ^(.*)$ https://recotek.org/$1 [R=301,L]
```

#### Nginx
```nginx
server {
    listen 80;
    server_name recotek.in www.recotek.in recotek.shop www.recotek.shop recotek.online www.recotek.online recotek.store www.recotek.store;
    return 301 https://recotek.org$request_uri;
}
```

### Method 3: HTML Meta Redirect (Fallback)

If other methods aren't available, create an `index.html` file on each alternate domain:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Redirecting to Recotek.org</title>
    <meta http-equiv="refresh" content="0; url=https://recotek.org">
    <link rel="canonical" href="https://recotek.org">
</head>
<body>
    <p>Redirecting to <a href="https://recotek.org">recotek.org</a>...</p>
    <script>window.location.href = "https://recotek.org";</script>
</body>
</html>
```

## Verification

After setting up redirects, verify they work correctly:

1. **Test each domain**:
   ```bash
   curl -I http://recotek.in
   curl -I http://recotek.shop
   curl -I http://recotek.online
   curl -I http://recotek.store
   ```

2. **Check for 301 status code** in the response headers:
   ```
   HTTP/1.1 301 Moved Permanently
   Location: https://recotek.org
   ```

3. **Test in browsers**:
   - Navigate to each alternate domain
   - Verify it redirects to `https://recotek.org`
   - Check that the URL changes to `recotek.org` in the address bar

## GitHub Pages Configuration

If hosting on GitHub Pages:

1. **Add custom domain** in repository settings:
   - Go to Settings → Pages
   - Custom domain: `recotek.org`
   - Enable "Enforce HTTPS"

2. **Configure DNS records**:
   ```
   Type: A
   Host: @
   Value: 185.199.108.153
   Value: 185.199.109.153
   Value: 185.199.110.153
   Value: 185.199.111.153

   Type: CNAME
   Host: www
   Value: realburhanhusain.github.io
   ```

3. **For alternate domains**, use your DNS provider's redirect feature to point to `recotek.org`.

## SSL/HTTPS Configuration

- Ensure all domains have valid SSL certificates
- Use Let's Encrypt for free SSL certificates
- Most DNS providers offer free SSL with their redirect services
- GitHub Pages provides automatic SSL for custom domains

## Monitoring

- Set up monitoring to check if redirects are working:
  - Use tools like UptimeRobot or Pingdom
  - Monitor for 301 redirect responses
  - Alert if any domain becomes unreachable

## Troubleshooting

**Redirect not working:**
- Check DNS propagation (can take 24-48 hours)
- Verify SSL certificates are valid
- Check firewall/security settings
- Clear browser cache and try incognito mode

**Mixed content warnings:**
- Ensure all redirects use HTTPS
- Check that destination domain (recotek.org) uses HTTPS

**Redirect loops:**
- Verify only alternate domains redirect to main domain
- Check that recotek.org doesn't redirect to itself

## Additional Notes

- Always use 301 (permanent) redirects for SEO benefits
- Keep ownership of all alternate domains to prevent misuse
- Consider setting up email forwarding if needed
- Monitor redirect traffic in Google Analytics
