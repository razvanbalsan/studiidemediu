# SEO Optimization Implementation Guide

This document outlines the SEO improvements implemented and additional recommendations for studiidemediu.ro.

## ✅ Implemented (HIGH Priority)

### 1. Sitemap
- ✅ Added `jekyll-sitemap` plugin to Gemfile
- ✅ Configured in `_config.yml`
- Automatically generates `/sitemap.xml`
- Run `bundle install` to install the plugin

### 2. Robots.txt
- ✅ Created `/robots.txt` file
- Allows all search engines
- References sitemap location
- Disallows internal/admin directories

### 3. Canonical URLs
- ✅ Added absolute canonical URLs in `_layouts/default.html`
- Format: `<link rel="canonical" href="https://studiidemediu.ro/page-url/">`
- Prevents duplicate content issues

### 4. Meta Descriptions & Keywords
- ✅ Enhanced descriptions for all main pages
- ✅ Added keyword meta tags to:
  - index.markdown (Acasă)
  - despre-noi.markdown
  - servicii.markdown
  - proiecte.markdown
  - contact.markdown
  - echipa.markdown
- ✅ Updated site description in `_config.yml` with more keywords

### 5. Render-Blocking Resources
- ✅ Optimized Google Fonts loading (async with fallback)
- ✅ Added preload for critical CSS
- ✅ Fonts load with `media="print"` then switch to `all`

### 6. Security Headers
- ✅ Added security meta tags in HTML head
- ✅ Created `.htaccess` with comprehensive security headers:
  - Strict-Transport-Security (HSTS)
  - X-Content-Type-Options
  - X-Frame-Options
  - X-XSS-Protection
  - Referrer-Policy
  - Content-Security-Policy

### 7. URL Canonicalization
- ✅ Created `.htaccess` with redirect rules:
  - Force HTTPS
  - Force non-www (studiidemediu.ro vs www.studiidemediu.ro)
  - Remove trailing slashes

## 🔄 To Implement (MEDIUM Priority)

### 8. Image Optimization

**Current Issues:**
- Images may not be in modern formats (WebP)
- Possible size/dimension issues

**Recommended Actions:**

#### Convert images to WebP format:
```bash
# Install cwebp if not installed (macOS)
brew install webp

# Convert all PNG images
for file in assets/images/**/*.png; do
  cwebp -q 85 "$file" -o "${file%.png}.webp"
done

# Convert all JPG/JPEG images
for file in assets/images/**/*.{jpg,jpeg}; do
  cwebp -q 85 "$file" -o "${file%.*}.webp"
done
```

#### Create responsive images with proper sizes:
```bash
# For team photos (currently 150px displayed)
convert original.jpg -resize 300x300 team-photo@2x.jpg  # For retina
convert original.jpg -resize 150x150 team-photo.jpg     # Standard

# For gallery images
convert original.jpg -resize 800x600 gallery-medium.jpg
convert original.jpg -resize 1600x1200 gallery-large.jpg
```

#### Update HTML to use picture element:
```html
<picture>
  <source srcset="image.webp" type="image/webp">
  <source srcset="image.jpg" type="image/jpeg">
  <img src="image.jpg" alt="Description" loading="lazy">
</picture>
```

### 9. Check Image Dimensions
Audit all `<img>` tags to ensure:
- Width and height attributes are set
- Displayed size matches actual size (no scaling in CSS)

## 📊 To Implement (LOW Priority)

### 10. Google Analytics

**Option 1: Google Analytics 4 (Recommended)**

1. Create GA4 property at https://analytics.google.com
2. Get Measurement ID (format: G-XXXXXXXXXX)
3. Add to `_config.yml`:
```yaml
google_analytics: G-XXXXXXXXXX
```

4. Add tracking code to `_layouts/default.html` before `</head>`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX', {
    'anonymize_ip': true,
    'cookie_flags': 'SameSite=None;Secure'
  });
</script>
```

**Option 2: Google Tag Manager (More Flexible)**

1. Create GTM container at https://tagmanager.google.com
2. Get Container ID (format: GTM-XXXXXX)
3. Add code to `_layouts/default.html`:

In `<head>`:
```html
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-XXXXXX');</script>
<!-- End Google Tag Manager -->
```

After opening `<body>`:
```html
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-XXXXXX"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<!-- End Google Tag Manager (noscript) -->
```

### 11. SPF Record for Email Security

This requires DNS configuration at your domain registrar:

1. Log into domain control panel
2. Add TXT record:
```
Type: TXT
Name: @
Value: v=spf1 include:_spf.google.com ~all
```

(Adjust based on your email provider)

### 12. Reduce HTTP Requests

**Current optimizations:**
- ✅ CSS is concatenated and compressed
- ✅ Fonts are preconnected

**Additional recommendations:**
- Combine SVG icons into a sprite sheet
- Use CSS instead of image icons where possible
- Enable HTTP/2 on server (multiple requests in parallel)
- Consider inlining critical CSS

## 🚀 Deployment Steps

### 1. Install Dependencies
```bash
cd /Users/razvanbalsan/Projects/studiidemediu
bundle install
```

### 2. Build Site
```bash
bundle exec jekyll build
```

### 3. Test Locally
```bash
bundle exec jekyll serve
# Visit http://localhost:4000
# Check /sitemap.xml
# Check /robots.txt
```

### 4. Upload to Server
- Upload `.htaccess` to site root
- Ensure all files are uploaded
- Test HTTPS redirect
- Verify canonical URLs point to correct domain

### 5. Verify in Google Search Console
1. Add property for https://studiidemediu.ro
2. Submit sitemap: https://studiidemediu.ro/sitemap.xml
3. Request indexing of key pages
4. Monitor coverage and errors

### 6. Test SEO
Use these tools:
- [Google PageSpeed Insights](https://pagespeed.web.dev/)
- [Google Mobile-Friendly Test](https://search.google.com/test/mobile-friendly)
- [SSL Labs](https://www.ssllabs.com/ssltest/)
- [Security Headers](https://securityheaders.com/)

## 📝 Configuration Updates

**Update URL in `_config.yml`:**
```yaml
url: "https://studiidemediu.ro"  # Your actual domain
```

**Verify in `.htaccess`:**
- Change domain in redirect rules if using www version
- Test redirects after deployment

## 🎯 SEO Best Practices Going Forward

### For New Pages/Posts:
Always include:
```yaml
---
title: "Descriptive Title with Keywords"
description: "Compelling 150-160 character description with keywords"
keywords: "keyword1, keyword2, keyword3"
---
```

### For Images:
- Always use descriptive `alt` attributes
- Include keywords naturally
- Compress before upload
- Use WebP format with fallback

### For Content:
- Use heading hierarchy (H1 → H2 → H3)
- Include keywords in first paragraph
- Use internal links to related content
- Keep URLs short and descriptive
- Update content regularly

## 📈 Monitoring

After implementation, monitor:
1. **Google Search Console**: Indexing, errors, search performance
2. **Google Analytics**: Traffic, bounce rate, user behavior
3. **PageSpeed Insights**: Performance scores
4. **Server logs**: 404 errors, redirect chains

## ⚠️ Important Notes

1. **Backup** before uploading `.htaccess` - incorrect rules can break site
2. **Test redirects** carefully - infinite loops can occur
3. **Monitor** after deployment for any issues
4. **Update** Google Analytics code with your actual Measurement ID
5. **Configure SPF** record based on your actual email provider

---

## Quick Reference: Files Modified

- ✅ `Gemfile` - Added jekyll-sitemap
- ✅ `_config.yml` - Added URL, enhanced description, sitemap plugin
- ✅ `_layouts/default.html` - Canonical URLs, security headers, optimized loading
- ✅ `robots.txt` - New file
- ✅ `.htaccess` - New file (for Apache servers)
- ✅ All main `.markdown` pages - Added descriptions and keywords

## Next Steps

1. Run `bundle install`
2. Test locally with `bundle exec jekyll serve`
3. Convert images to WebP format
4. Set up Google Analytics
5. Upload to production server
6. Submit sitemap to Google Search Console
7. Monitor and iterate based on analytics
