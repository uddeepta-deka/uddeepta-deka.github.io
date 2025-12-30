# SEO, Performance & Accessibility Implementation Checklist

## ✅ **COMPLETED IMPROVEMENTS**

### **SEO Enhancements:**
- [x] Enhanced meta descriptions in _config.yml
- [x] Added keywords for search engines
- [x] Created comprehensive SEO meta tags include file
- [x] Added Open Graph tags for social media sharing
- [x] Added Twitter Card meta tags
- [x] Implemented JSON-LD structured data (Schema.org Person)
- [x] Added page-specific descriptions and keywords
- [x] Added canonical URLs
- [x] Set up language tags

### **Accessibility Improvements:**
- [x] Added skip-to-content link for keyboard navigation
- [x] Enhanced navigation with ARIA roles and labels
- [x] Added descriptive alt text to profile images
- [x] Implemented ARIA labels on all social links
- [x] Added sr-only spans for screen readers
- [x] Set proper semantic HTML (role="main", role="banner")
- [x] Added aria-current="page" for active nav items
- [x] Fixed heading hierarchy (h1 → p, not h1 → h2)

### **Performance Optimizations:**
- [x] Added font preloading
- [x] Optimized Google Fonts loading (media="print" trick)
- [x] Added DNS prefetch for external resources
- [x] Added width/height to images (prevents layout shift)
- [x] Implemented loading="eager" for above-fold images

---

## 📋 **TODO: ACTIONS REQUIRED**

### **🎨 Critical (Do First):**

#### 1. Create Social Preview Image
**File:** `assets/images/social-preview.jpg`
- **Size:** 1200x630 pixels
- **Content:** Your photo + name + tagline
- **Format:** JPG, under 300KB
- **Tool:** Use Canva (https://www.canva.com/) with "Social Media" template

**How to create:**
1. Go to Canva.com
2. Search "Open Graph" or create 1200x630px custom size
3. Add your profile photo (circular)
4. Add text: "Uddeepta Deka"
5. Add subtitle: "Gravitational Wave Physicist | ICTS-TIFR"
6. Use blue gradient background (#2563eb to #0ea5e9)
7. Download as JPG, compress with TinyPNG
8. Upload to `assets/images/social-preview.jpg`

#### 2. Optimize Existing Images
**Action:** Compress all images in `assets/images/`
- Use TinyPNG: https://tinypng.com/
- Target: Reduce file sizes by 60-70%
- Maintain visual quality

**Steps:**
```bash
# 1. Backup originals
cp -r assets/images assets/images-original

# 2. Upload to TinyPNG and download compressed versions
# Or use command line tool

# 3. Replace originals with compressed versions
```

#### 3. Add Image Dimensions
**Action:** Find all `<img>` tags and add width/height

**Example:**
```html
<!-- Before -->
<img src="image.jpg" alt="Description">

<!-- After -->
<img src="image.jpg" alt="Description" width="400" height="400">
```

**Files to check:**
- `about.md` - Profile image
- `research.md` - Any images
- `_includes/header.html` - Already done ✅
- Blog posts - Check all posts

---

### **📊 Important (Do This Week):**

#### 4. Test & Validate SEO
**Actions:**
1. **Test with Google Rich Results:**
   - Visit: https://search.google.com/test/rich-results
   - Enter: https://uddeepta-deka.github.io/
   - Check for structured data errors

2. **Test with Facebook Debugger:**
   - Visit: https://developers.facebook.com/tools/debug/
   - Enter your URL
   - Check Open Graph preview
   - Click "Scrape Again" to refresh cache

3. **Test with Twitter Card Validator:**
   - Visit: https://cards-dev.twitter.com/validator
   - Enter your URL
   - Check card preview

4. **Google PageSpeed Insights:**
   - Visit: https://pagespeed.web.dev/
   - Test your site
   - Target: 90+ score

#### 5. Enable Google Analytics (Optional)
**Action:** Uncomment and add your GA tracking ID

**File:** `_config.yml`
```yaml
# Current:
# analytics-google: 'UA-MYANALYTICS'

# Change to:
analytics-google: 'G-XXXXXXXXXX'  # Your GA4 measurement ID
```

**Get tracking ID:**
1. Create account: https://analytics.google.com/
2. Set up property for your site
3. Copy Measurement ID (starts with G-)
4. Add to _config.yml

#### 6. Create robots.txt (Enhanced)
**File:** `robots.txt` (already exists, enhance it)

**Add:**
```
User-agent: *
Allow: /

# Sitemaps
Sitemap: https://uddeepta-deka.github.io/sitemap.xml
Sitemap: https://uddeepta-deka.github.io/feed.xml

# Crawl rate
Crawl-delay: 0

# Block specific bots (optional)
User-agent: AhrefsBot
Crawl-delay: 10
```

#### 7. Verify sitemap.xml
**Action:** Ensure Jekyll generates sitemap automatically

**Check:**
- Visit: https://uddeepta-deka.github.io/sitemap.xml
- Should show all pages
- If missing, Jekyll should auto-generate (jekyll-seo-tag plugin)

---

### **🎯 Optional (Nice to Have):**

#### 8. Add Favicon Set
**Current:** Basic favicon via `_includes/favicon.html`

**Enhance with full set:**
```html
<!-- Add to favicon.html -->
<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/assets/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/assets/apple-touch-icon.png">
<link rel="manifest" href="/site.webmanifest">
```

**Generate favicons:**
- Use: https://realfavicongenerator.net/
- Upload your profile photo or logo
- Download package
- Upload to `assets/` folder

#### 9. Implement Dark Mode Properly
**Current:** Auto dark mode in _config.yml

**Enhance:**
- Add manual toggle button
- Save preference in localStorage
- Test contrast ratios for dark mode

#### 10. Add Schema.org Article Markup for Blog Posts
**File:** `_layouts/post.html` (if you publish blog posts)

**Add:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "{{ page.title }}",
  "author": {
    "@type": "Person",
    "name": "{{ site.title }}"
  },
  "datePublished": "{{ page.date | date_to_xmlschema }}",
  "description": "{{ page.excerpt | strip_html | truncate: 160 }}",
  "image": "{{ page.image | absolute_url }}"
}
</script>
```

---

## 🧪 **TESTING CHECKLIST**

### **Accessibility Testing:**
- [ ] Test with screen reader (NVDA/JAWS on Windows, VoiceOver on Mac)
- [ ] Test keyboard navigation (Tab, Enter, Space, Arrow keys)
- [ ] Check skip link appears on Tab
- [ ] Verify all images have descriptive alt text
- [ ] Test with browser zoom at 200%
- [ ] Check color contrast with WebAIM tool

**Tools:**
- WAVE: https://wave.webaim.org/
- aXe DevTools: Chrome extension
- Lighthouse: Built into Chrome DevTools

### **SEO Testing:**
- [ ] Google Search Console (submit sitemap)
- [ ] Google Rich Results Test
- [ ] Facebook Sharing Debugger
- [ ] Twitter Card Validator
- [ ] Test page titles in search results
- [ ] Verify meta descriptions appear correctly

**Tools:**
- Google Search Console: https://search.google.com/search-console
- PageSpeed Insights: https://pagespeed.web.dev/

### **Performance Testing:**
- [ ] Google PageSpeed Insights (target: 90+)
- [ ] WebPageTest (target: A grade)
- [ ] Check Core Web Vitals (LCP < 2.5s, FID < 100ms, CLS < 0.1)
- [ ] Test on 3G network (throttle in DevTools)
- [ ] Test on mobile device
- [ ] Check total page size (target: < 1MB)

**Tools:**
- Chrome DevTools > Lighthouse
- WebPageTest: https://www.webpagetest.org/
- GTmetrix: https://gtmetrix.com/

### **Cross-Browser Testing:**
- [ ] Chrome (desktop & mobile)
- [ ] Firefox
- [ ] Safari (macOS & iOS)
- [ ] Edge
- [ ] Test on different screen sizes (320px, 768px, 1920px)

---

## 📊 **EXPECTED METRICS**

### **SEO Metrics:**
- **Google Page Rank:** Indexed within 1-2 weeks
- **Structured Data:** Valid Person schema
- **Rich Snippets:** Social links, name, occupation
- **Search Appearance:** Title, description, site links

### **Performance Metrics (Target):**
- **Lighthouse Score:** 95+ (Performance), 100 (Accessibility, Best Practices, SEO)
- **LCP (Largest Contentful Paint):** < 1.5s
- **FID (First Input Delay):** < 50ms
- **CLS (Cumulative Layout Shift):** < 0.1
- **Total Page Size:** < 500KB
- **Time to Interactive:** < 2s

### **Accessibility Metrics:**
- **WCAG Level:** AA compliant
- **Contrast Ratio:** 4.5:1 minimum (text)
- **Keyboard Navigation:** 100% accessible
- **Screen Reader:** All content accessible

---

## 🎯 **PRIORITY ACTION PLAN**

### **Week 1 (Critical):**
1. ✅ Create social preview image
2. ✅ Optimize all images (compress)
3. ✅ Add width/height to all images
4. ✅ Test with Facebook/Twitter debuggers

### **Week 2 (Important):**
5. ⏳ Test with Google Rich Results
6. ⏳ Enable Google Analytics (optional)
7. ⏳ Run full accessibility audit
8. ⏳ Test on mobile devices

### **Week 3 (Polish):**
9. ⏳ Create full favicon set
10. ⏳ Add blog post schema markup
11. ⏳ Set up Google Search Console
12. ⏳ Final performance testing

---

## 📈 **MONITORING & MAINTENANCE**

### **Monthly:**
- Check Google Search Console for errors
- Review Google Analytics traffic
- Test PageSpeed score
- Check broken links

### **Quarterly:**
- Update meta descriptions if needed
- Refresh social preview image
- Re-audit accessibility
- Update structured data

### **Annually:**
- Review and update keywords
- Optimize images again (new tools/formats)
- Update to latest web standards
- Full SEO audit

---

## 🔗 **USEFUL RESOURCES**

### **SEO:**
- Google Search Central: https://developers.google.com/search
- Schema.org: https://schema.org/
- Open Graph Protocol: https://ogp.me/

### **Accessibility:**
- WCAG Guidelines: https://www.w3.org/WAI/WCAG21/quickref/
- WebAIM: https://webaim.org/
- A11y Project: https://www.a11yproject.com/

### **Performance:**
- Web.dev: https://web.dev/fast/
- Core Web Vitals: https://web.dev/vitals/
- Image Optimization: https://web.dev/fast/#optimize-your-images

### **Testing Tools:**
- Lighthouse: Built into Chrome
- WAVE: https://wave.webaim.org/
- PageSpeed Insights: https://pagespeed.web.dev/
- GTmetrix: https://gtmetrix.com/

---

**Last Updated:** 2025
**Implementation Status:** In Progress 🚧
**Target Completion:** Week 3
