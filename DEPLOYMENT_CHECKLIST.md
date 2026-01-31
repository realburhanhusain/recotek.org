# Deployment Checklist for Recotek.org

Use this checklist to ensure successful deployment of the Recotek.org website.

## Pre-Deployment Checklist

- [ ] Repository is pushed to GitHub
- [ ] All files are committed (run `git status` to verify)
- [ ] README.md is updated
- [ ] CNAME file contains `recotek.org`

## GitHub Pages Setup

- [ ] Navigate to repository Settings → Pages
- [ ] Set source to "Deploy from a branch"
- [ ] Select branch: `main` (or `master`)
- [ ] Select folder: `/ (root)`
- [ ] Click Save
- [ ] Add custom domain: `recotek.org`
- [ ] Wait for DNS check to complete

## DNS Configuration (Main Domain)

### At your domain registrar for recotek.org:

- [ ] Add A records for apex domain:
  - [ ] `185.199.108.153`
  - [ ] `185.199.109.153`
  - [ ] `185.199.110.153`
  - [ ] `185.199.111.153`

- [ ] Add CNAME record for www:
  - [ ] Host: `www`
  - [ ] Value: `realburhanhusain.github.io.`

- [ ] Save DNS changes

## Alternate Domain Redirects

For each domain (recotek.in, recotek.shop, recotek.online, recotek.store):

### Option 1: DNS Provider Redirect (Recommended)
- [ ] Log into domain registrar
- [ ] Find "Domain Forwarding" or "URL Redirect" settings
- [ ] Set up 301 permanent redirect to `https://recotek.org`
- [ ] Enable HTTPS forwarding
- [ ] Save changes

### Option 2: Host Redirect Page
- [ ] Set up basic hosting for domain
- [ ] Upload `redirect.html` file
- [ ] Point domain DNS to hosting
- [ ] Test redirect works

## Post-Deployment Verification

### DNS Propagation (24-48 hours)
- [ ] Check DNS propagation: https://dnschecker.org/
- [ ] Verify A records resolve correctly
- [ ] Verify CNAME record resolves correctly

### SSL Certificate
- [ ] Wait for GitHub Pages to provision SSL (automatic)
- [ ] Check "Enforce HTTPS" in GitHub Pages settings
- [ ] Verify HTTPS works: https://recotek.org
- [ ] Check for green padlock in browser

### Main Domain Testing
- [ ] Visit https://recotek.org
- [ ] Verify website loads correctly
- [ ] Test on desktop browser
- [ ] Test on mobile browser
- [ ] Test on tablet
- [ ] Check all navigation links work
- [ ] Verify contact form displays correctly
- [ ] Check footer links
- [ ] Test smooth scrolling

### Redirect Testing
- [ ] Test https://recotek.in redirects to https://recotek.org
- [ ] Test https://recotek.shop redirects to https://recotek.org
- [ ] Test https://recotek.online redirects to https://recotek.org
- [ ] Test https://recotek.store redirects to https://recotek.org
- [ ] Verify redirects are 301 (permanent)
- [ ] Check www versions redirect correctly

### Performance Testing
- [ ] Run Google PageSpeed Insights: https://pagespeed.web.dev/
- [ ] Run GTmetrix: https://gtmetrix.com/
- [ ] Check loading time < 3 seconds
- [ ] Verify mobile performance score

### SEO Verification
- [ ] Check meta tags are present
- [ ] Verify Open Graph tags
- [ ] Submit sitemap to Google Search Console
- [ ] Test social media sharing

### Browser Testing
- [ ] Chrome/Edge (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Mobile Safari (iOS)
- [ ] Chrome Mobile (Android)

### Functionality Testing
- [ ] Mobile menu toggle works
- [ ] Smooth scroll navigation works
- [ ] All sections are visible
- [ ] Animations play correctly
- [ ] Counter animations work
- [ ] Contact form can be submitted
- [ ] No console errors
- [ ] No 404 errors

## Post-Launch Tasks

### Analytics Setup
- [ ] Set up Google Analytics
- [ ] Add tracking code to website
- [ ] Verify tracking is working
- [ ] Set up goals and conversions

### Monitoring Setup
- [ ] Set up uptime monitoring (UptimeRobot, Pingdom)
- [ ] Configure alerts for downtime
- [ ] Monitor all domains including redirects
- [ ] Set up SSL certificate expiration alerts

### Security
- [ ] Enable two-factor authentication on GitHub
- [ ] Enable two-factor authentication on domain registrar
- [ ] Review repository access permissions
- [ ] Document recovery procedures

### Documentation
- [ ] Update internal documentation
- [ ] Document any custom configurations
- [ ] Create runbook for common issues
- [ ] Document rollback procedure

### Communication
- [ ] Announce website launch
- [ ] Update social media profiles
- [ ] Update business cards/materials
- [ ] Notify stakeholders

## Troubleshooting Reference

### Common Issues

**DNS not resolving:**
- Wait 24-48 hours for propagation
- Clear local DNS cache: `ipconfig /flushdns` (Windows) or `sudo dscacheutil -flushcache` (Mac)
- Check DNS with: `nslookup recotek.org`

**SSL not working:**
- Ensure DNS is properly configured first
- Wait up to 24 hours after DNS is active
- Try removing and re-adding custom domain in GitHub Pages

**Website not loading:**
- Verify GitHub Pages is enabled
- Check branch and folder settings
- Ensure index.html is in root directory
- Check repository is public or you have GitHub Pro

**Redirects not working:**
- Verify redirect configuration at domain registrar
- Check for redirect loops
- Test with curl: `curl -I https://recotek.in`
- Clear browser cache

## Support Contacts

- **GitHub Pages Support:** https://docs.github.com/en/pages
- **Domain Registrar Support:** [Your registrar's support page]
- **DNS Help:** https://dnschecker.org/

## Success Criteria

✅ Main domain (recotek.org) loads correctly with HTTPS
✅ All alternate domains redirect to main domain
✅ Website is mobile responsive
✅ All features work as expected
✅ Performance scores > 80 on PageSpeed Insights
✅ No console errors or broken links
✅ SSL certificate is active and valid
✅ Analytics tracking is working

---

**Deployment Date:** _________________

**Deployed By:** _________________

**Verified By:** _________________

**Notes:**
_______________________________________________________
_______________________________________________________
_______________________________________________________
