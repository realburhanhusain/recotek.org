# Deployment Guide for Recotek.org

## Quick Start

This website is ready to deploy to GitHub Pages or any static hosting service.

## GitHub Pages Deployment

### Step 1: Configure Repository Settings

1. Go to your repository on GitHub
2. Click on "Settings"
3. Navigate to "Pages" in the left sidebar
4. Under "Source", select "Deploy from a branch"
5. Select branch: `main` (or `master`)
6. Select folder: `/ (root)`
7. Click "Save"

### Step 2: Add Custom Domain

1. In the same "Pages" settings
2. Under "Custom domain", enter: `recotek.org`
3. Click "Save"
4. Check "Enforce HTTPS" (this will enable after DNS is configured)

### Step 3: Configure DNS Records

Go to your domain registrar (where you purchased recotek.org) and add these DNS records:

**For apex domain (recotek.org):**
```
Type: A
Name: @
Value: 185.199.108.153

Type: A
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153
```

**For www subdomain:**
```
Type: CNAME
Name: www
Value: realburhanhusain.github.io.
```

### Step 4: Wait for DNS Propagation

- DNS changes can take 24-48 hours to propagate globally
- Use [DNS Checker](https://dnschecker.org/) to monitor propagation
- Once propagated, GitHub will automatically provision SSL certificate

### Step 5: Configure Alternate Domains

For each alternate domain (recotek.in, recotek.shop, recotek.online, recotek.store):

**Option A: Domain Forwarding (Recommended)**
1. Log into your domain registrar
2. Find "Domain Forwarding" or "URL Redirect" settings
3. Set up 301 permanent redirect to `https://recotek.org`
4. Enable HTTPS

**Option B: Host Redirect Page**
1. Create a simple hosting for each domain
2. Upload the `redirect.html` file
3. Point domain to hosting

## Alternative Deployment Options

### Netlify

1. Log in to [Netlify](https://netlify.com)
2. Click "Add new site" → "Import an existing project"
3. Connect your GitHub repository
4. Build settings:
   - Build command: (leave empty)
   - Publish directory: `/`
5. Click "Deploy site"
6. Add custom domain: `recotek.org` in Site settings → Domain management

### Vercel

1. Log in to [Vercel](https://vercel.com)
2. Click "Add New..." → "Project"
3. Import your GitHub repository
4. Framework Preset: Other
5. Root Directory: ./
6. Click "Deploy"
7. Add domain in Settings → Domains

### AWS S3 + CloudFront

1. Create S3 bucket named `recotek.org`
2. Enable static website hosting
3. Upload all files
4. Set bucket policy for public read access
5. Create CloudFront distribution
6. Configure Route 53 for DNS
7. Request SSL certificate in Certificate Manager

## Verification Steps

After deployment:

1. **Check Main Domain**:
   ```bash
   curl -I https://recotek.org
   ```
   Should return `200 OK`

2. **Check Redirects**:
   ```bash
   curl -I https://recotek.in
   curl -I https://recotek.shop
   curl -I https://recotek.online
   curl -I https://recotek.store
   ```
   Should return `301 Moved Permanently` with `Location: https://recotek.org`

3. **Test in Browser**:
   - Visit https://recotek.org
   - Check all links work
   - Test mobile responsiveness
   - Verify SSL certificate (green padlock)
   - Test alternate domains redirect

4. **Performance Check**:
   - Use [PageSpeed Insights](https://pagespeed.web.dev/)
   - Use [GTmetrix](https://gtmetrix.com/)
   - Check loading time < 3 seconds

## Troubleshooting

### SSL Certificate Not Working
- Wait 24 hours after DNS configuration
- Ensure CNAME file contains exactly `recotek.org`
- Check DNS records are correct
- In GitHub Pages settings, try removing and re-adding custom domain

### Domain Not Resolving
- Use `nslookup recotek.org` to check DNS
- Use `dig recotek.org` to see DNS records
- Check DNS propagation at dnschecker.org
- Wait up to 48 hours for global propagation

### 404 Error on GitHub Pages
- Ensure `index.html` is in root directory
- Check branch name is correct in Pages settings
- Verify repository is public or you have GitHub Pro
- Clear browser cache and try incognito mode

### Redirect Not Working
- Verify redirect is 301 (permanent) not 302 (temporary)
- Check SSL certificates on alternate domains
- Test with curl to see actual HTTP headers
- Ensure no redirect loops

## Maintenance

### Updating Content
1. Edit files locally
2. Commit changes: `git commit -am "Update content"`
3. Push to GitHub: `git push origin main`
4. GitHub Pages will automatically rebuild (takes 1-2 minutes)

### Monitoring
- Set up Google Analytics for traffic monitoring
- Use UptimeRobot or similar for uptime monitoring
- Check regularly that redirects still work
- Monitor SSL certificate expiration (auto-renewed by GitHub)

## Security Best Practices

- Keep domain registrar account secure with 2FA
- Use strong passwords
- Regularly check DNS records haven't been modified
- Monitor for any unauthorized changes to repository
- Keep GitHub account secure with 2FA
- Review repository access regularly

## Support

For deployment issues:
- GitHub Pages: [GitHub Pages Documentation](https://docs.github.com/en/pages)
- DNS: Contact your domain registrar support
- Repository issues: Open an issue on GitHub

---

Last updated: 2026-01-31
