# Recotek.org - Cryptocurrency & Blockchain Website

Welcome to Recotek.org, a professional cryptocurrency and blockchain technology website.

## 🚀 Live Website

Visit: [https://recotek.org](https://recotek.org)

## 📋 Overview

Recotek is a modern, responsive website designed for cryptocurrency and blockchain technology solutions. The website features:

- **Modern Design**: Clean, professional design with cryptocurrency-themed styling
- **Fully Responsive**: Works seamlessly on desktop, tablet, and mobile devices
- **Fast Performance**: Optimized HTML, CSS, and JavaScript for quick loading
- **SEO Optimized**: Proper meta tags and semantic HTML structure
- **Multi-Domain Support**: Configured for multiple domain redirects

## 🌐 Domains

Main domain: **recotek.org**

Alternate domains (configured to redirect to main domain):
- recotek.in
- recotek.shop
- recotek.online
- recotek.store

See [DOMAIN_REDIRECTS.md](DOMAIN_REDIRECTS.md) for detailed redirect configuration instructions.

## 🎨 Features

### Website Sections

1. **Hero Section**
   - Eye-catching headline with gradient text
   - Call-to-action buttons
   - Live statistics display
   - Animated cryptocurrency icons

2. **Features Section**
   - 6 key features with icons
   - Hover animations
   - Responsive grid layout

3. **About Section**
   - Company information
   - Feature highlights
   - 3D animated graphics

4. **Services Section**
   - Service offerings
   - Icon-based cards
   - Professional presentation

5. **Contact Section**
   - Contact information
   - Contact form
   - Responsive layout

6. **Footer**
   - Navigation links
   - Social media links
   - Legal links
   - Copyright information

## 🛠️ Technology Stack

- **HTML5**: Semantic markup
- **CSS3**: Modern styling with animations and gradients
- **JavaScript (Vanilla)**: Interactive features and animations
- **Font Awesome**: Icon library
- **Google Fonts**: Inter font family

## 📁 File Structure

```
recotek.org/
├── index.html              # Main HTML file
├── css/
│   └── style.css          # Main stylesheet
├── js/
│   └── script.js          # JavaScript functionality
├── CNAME                  # GitHub Pages custom domain
├── redirect.html          # Example redirect page for alternate domains
├── DOMAIN_REDIRECTS.md    # Domain redirect documentation
└── README.md              # This file
```

## 🚀 Deployment

### GitHub Pages (Recommended)

1. **Enable GitHub Pages**:
   - Go to repository Settings → Pages
   - Source: Deploy from main branch
   - Root directory: / (root)
   - Custom domain: recotek.org
   - Enable "Enforce HTTPS"

2. **Configure DNS** (at your domain registrar):
   ```
   Type: A
   Host: @
   Values:
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153

   Type: CNAME
   Host: www
   Value: <your-github-username>.github.io
   ```

3. **Wait for DNS propagation** (up to 24-48 hours)

4. **Verify**:
   - Visit https://recotek.org
   - Check SSL certificate is active
   - Test mobile responsiveness

### Alternative Hosting Options

The website can also be hosted on:
- Netlify
- Vercel
- AWS S3 + CloudFront
- Any static web hosting service

## 🔧 Local Development

1. **Clone the repository**:
   ```bash
   git clone https://github.com/realburhanhusain/recotek.org.git
   cd recotek.org
   ```

2. **Open in browser**:
   - Simply open `index.html` in your web browser
   - Or use a local server:
     ```bash
     # Python 3
     python -m http.server 8000
     
     # Node.js (with http-server)
     npx http-server
     ```

3. **Access**:
   - Navigate to `http://localhost:8000`

## 🎨 Customization

### Changing Colors

Edit the CSS variables in `css/style.css`:

```css
:root {
    --primary-color: #f7931a;      /* Orange/Bitcoin color */
    --secondary-color: #4a90e2;    /* Blue */
    --dark-bg: #0f1419;            /* Dark background */
    --dark-secondary: #1a1f2e;     /* Secondary dark */
    /* ... */
}
```

### Updating Content

- Edit `index.html` to change text content
- Modify sections, add new features, or update information
- Update contact information in the Contact section

### Adding New Sections

1. Add HTML in `index.html`
2. Add corresponding styles in `css/style.css`
3. Add any JavaScript functionality in `js/script.js`

## 📱 Mobile Responsiveness

The website is fully responsive with breakpoints at:
- Desktop: 1200px+
- Tablet: 768px - 1199px
- Mobile: < 768px

## 🔒 Security

- All external resources loaded over HTTPS
- No inline scripts or styles (CSP friendly)
- Form validation included
- Safe redirect configurations

## 📈 SEO

- Semantic HTML5 structure
- Meta tags for search engines
- Open Graph tags for social sharing
- Mobile-friendly design
- Fast loading times
- Accessible markup

## 🤝 Contributing

This is a private project for Recotek.org. For any issues or suggestions, please contact the repository owner.

## 📄 License

Copyright © 2026 Recotek. All rights reserved.

## 📞 Support

For questions or support:
- Email: info@recotek.org
- Website: https://recotek.org

---

Built with ❤️ for the cryptocurrency community
