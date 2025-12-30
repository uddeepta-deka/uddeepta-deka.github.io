# Quick Reference: Code Snippets for Common Tasks

## 🎯 **Copy-Paste Ready Code**

---

## 1️⃣ **Adding New Pages with SEO**

### **Create new page with full SEO:**

**File:** `new-page.md`
```markdown
---
title: Page Title
layout: page
description: "Brief description for search engines (150-160 characters). Include key terms naturally."
keywords: "keyword1, keyword2, keyword3, related terms, your name"
image: assets/images/custom-preview.jpg  # Optional: page-specific preview
---

# Your Content Here

Write your content in Markdown...
```

---

## 2️⃣ **Accessible Image Patterns**

### **Standard Image (with lazy loading):**
```html
<img src="assets/images/filename.jpg" 
     alt="Descriptive text explaining what's in the image" 
     width="800" 
     height="600"
     loading="lazy">
```

### **Hero Image (above the fold):**
```html
<img src="assets/images/hero.jpg" 
     alt="Uddeepta Deka at ICTS-TIFR presenting gravitational wave research" 
     width="1200" 
     height="800"
     loading="eager">
```

### **Responsive Image (multiple sizes):**
```html
<img src="assets/images/photo-800w.jpg"
     srcset="assets/images/photo-400w.jpg 400w,
             assets/images/photo-800w.jpg 800w,
             assets/images/photo-1200w.jpg 1200w"
     sizes="(max-width: 640px) 100vw,
            (max-width: 1024px) 80vw,
            800px"
     alt="Descriptive alt text"
     width="800"
     height="600"
     loading="lazy">
```

### **Modern Format with Fallback (WebP + JPG):**
```html
<picture>
  <source srcset="assets/images/photo.webp" type="image/webp">
  <source srcset="assets/images/photo.jpg" type="image/jpeg">
  <img src="assets/images/photo.jpg" 
       alt="Descriptive alt text"
       width="800"
       height="600"
       loading="lazy">
</picture>
```

---

## 3️⃣ **Accessible Link Patterns**

### **External Link (opens in new tab):**
```html
<a href="https://external-site.com" 
   target="_blank" 
   rel="noopener noreferrer"
   aria-label="Visit external site (opens in new tab)">
    Link Text
</a>
```

### **Download Link:**
```html
<a href="assets/documents/paper.pdf" 
   download
   aria-label="Download PDF (2.5 MB)">
    Download Paper
</a>
```

### **Email Link:**
```html
<a href="mailto:email@example.com"
   aria-label="Send email to email@example.com">
    Contact Me
</a>
```

### **Phone Link (mobile):**
```html
<a href="tel:+1234567890"
   aria-label="Call phone number +1 234 567 8900">
    +1 (234) 567-8900
</a>
```

---

## 4️⃣ **Accessible Buttons**

### **Primary Button:**
```html
<button type="button" 
        class="btn btn-primary"
        aria-label="Submit form"
        data-testid="submit-btn">
    Submit
</button>
```

### **Link Styled as Button:**
```html
<a href="/research" 
   class="btn btn-primary"
   role="button"
   aria-label="View research publications"
   data-testid="view-research-btn">
    View Research
</a>
```

---

## 5️⃣ **Semantic HTML Patterns**

### **Article Structure:**
```html
<article role="article" aria-labelledby="article-title">
    <header>
        <h2 id="article-title">Article Title</h2>
        <p class="meta">
            <time datetime="2025-01-15">January 15, 2025</time>
        </p>
    </header>
    
    <div class="content">
        <p>Article content...</p>
    </div>
    
    <footer>
        <p>Author information or metadata</p>
    </footer>
</article>
```

### **Navigation Section:**
```html
<nav role="navigation" aria-label="Section navigation">
    <ul>
        <li><a href="#section1">Section 1</a></li>
        <li><a href="#section2">Section 2</a></li>
    </ul>
</nav>
```

### **Section with Heading:**
```html
<section aria-labelledby="section-heading">
    <h2 id="section-heading">Section Title</h2>
    <p>Section content...</p>
</section>
```

---

## 6️⃣ **ARIA Patterns**

### **Visually Hidden Text (screen reader only):**
```html
<span class="sr-only">
    Additional context for screen readers
</span>

<!-- CSS for sr-only (already in social-links.html) -->
<style>
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
}
</style>
```

### **Loading State:**
```html
<button aria-busy="true" aria-label="Loading, please wait">
    <span aria-hidden="true">⏳</span>
    Loading...
</button>
```

### **Expanded/Collapsed State:**
```html
<button aria-expanded="false" 
        aria-controls="content-id"
        id="toggle-btn">
    Show More
</button>

<div id="content-id" 
     aria-labelledby="toggle-btn"
     hidden>
    Hidden content...
</div>
```

---

## 7️⃣ **Meta Tags for New Pages**

### **Add to page frontmatter:**
```yaml
---
title: Your Page Title
description: "SEO-optimized description 150-160 characters with relevant keywords"
keywords: "keyword1, keyword2, keyword3, your name, research area"
image: assets/images/page-preview.jpg  # Optional
---
```

### **For Blog Posts:**
```yaml
---
title: "Blog Post Title"
description: "Post summary for search engines and social media"
date: 2025-01-15
author: Uddeepta Deka
tags: [gravitational-waves, research, physics]
image: assets/blog_images/post-image.jpg
---
```

---

## 8️⃣ **Forms (Accessible)**

### **Contact Form Pattern:**
```html
<form action="/submit" method="POST" aria-label="Contact form">
    <div class="form-group">
        <label for="name">
            Name <span aria-label="required">*</span>
        </label>
        <input type="text" 
               id="name" 
               name="name"
               required
               aria-required="true"
               aria-describedby="name-help">
        <small id="name-help">Enter your full name</small>
    </div>
    
    <div class="form-group">
        <label for="email">
            Email <span aria-label="required">*</span>
        </label>
        <input type="email" 
               id="email" 
               name="email"
               required
               aria-required="true"
               aria-describedby="email-help">
        <small id="email-help">We'll never share your email</small>
    </div>
    
    <div class="form-group">
        <label for="message">Message</label>
        <textarea id="message" 
                  name="message"
                  rows="5"
                  aria-describedby="message-help"></textarea>
        <small id="message-help">Optional: Add a message</small>
    </div>
    
    <button type="submit" 
            class="btn btn-primary"
            aria-label="Submit contact form">
        Send Message
    </button>
</form>
```

---

## 9️⃣ **Tables (Accessible)**

### **Data Table:**
```html
<table role="table" aria-label="Publication data">
    <caption>Recent Publications (2024-2025)</caption>
    <thead>
        <tr>
            <th scope="col">Title</th>
            <th scope="col">Journal</th>
            <th scope="col">Year</th>
            <th scope="col">Citations</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Paper Title Here</td>
            <td>Physical Review D</td>
            <td>2025</td>
            <td>15</td>
        </tr>
    </tbody>
</table>
```

---

## 🔟 **Video Embed (Accessible)**

### **YouTube Video:**
```html
<div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/VIDEO_ID"
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
            title="Descriptive title of the video content"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
            loading="lazy">
    </iframe>
</div>
```

---

## 1️⃣1️⃣ **Custom Page-Specific Schema**

### **Add to specific page (e.g., research.md):**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "CollectionPage",
  "name": "Research Publications",
  "description": "List of research publications by Uddeepta Deka",
  "author": {
    "@type": "Person",
    "name": "Uddeepta Deka",
    "url": "https://uddeepta-deka.github.io"
  },
  "hasPart": [
    {
      "@type": "ScholarlyArticle",
      "headline": "Surrogate modeling of gravitational waves",
      "author": "Uddeepta Deka",
      "datePublished": "2025",
      "publisher": {
        "@type": "Organization",
        "name": "American Physical Society"
      }
    }
  ]
}
</script>
```

---

## 1️⃣2️⃣ **Performance Optimization Snippets**

### **Preload Critical Resources:**
```html
<head>
    <!-- Preload critical CSS -->
    <link rel="preload" href="/assets/main.css" as="style">
    
    <!-- Preload critical font -->
    <link rel="preload" href="/assets/fonts/Inter-Regular.woff2" as="font" type="font/woff2" crossorigin>
    
    <!-- DNS prefetch for external resources -->
    <link rel="dns-prefetch" href="//fonts.googleapis.com">
</head>
```

### **Async Load Non-Critical CSS:**
```html
<link rel="stylesheet" 
      href="/assets/non-critical.css" 
      media="print" 
      onload="this.media='all'">
<noscript>
    <link rel="stylesheet" href="/assets/non-critical.css">
</noscript>
```

---

## 1️⃣3️⃣ **Social Share Buttons**

### **Share Links (No JavaScript):**
```html
<div class="share-buttons" role="navigation" aria-label="Share this page">
    <!-- Twitter -->
    <a href="https://twitter.com/intent/tweet?url={{ page.url | absolute_url }}&text={{ page.title | uri_escape }}"
       target="_blank"
       rel="noopener noreferrer"
       aria-label="Share on Twitter (opens in new tab)"
       class="btn btn-outline">
        <i class="fa-brands fa-twitter" aria-hidden="true"></i> Tweet
    </a>
    
    <!-- LinkedIn -->
    <a href="https://www.linkedin.com/sharing/share-offsite/?url={{ page.url | absolute_url }}"
       target="_blank"
       rel="noopener noreferrer"
       aria-label="Share on LinkedIn (opens in new tab)"
       class="btn btn-outline">
        <i class="fa-brands fa-linkedin" aria-hidden="true"></i> Share
    </a>
    
    <!-- Email -->
    <a href="mailto:?subject={{ page.title | uri_escape }}&body=Check out this page: {{ page.url | absolute_url }}"
       aria-label="Share via email"
       class="btn btn-outline">
        <i class="fa-regular fa-envelope" aria-hidden="true"></i> Email
    </a>
</div>
```

---

## 📚 **Quick Testing Commands**

### **Test Accessibility (WAVE):**
```
Visit: https://wave.webaim.org/
Enter: https://uddeepta-deka.github.io/
```

### **Test SEO (Google):**
```
Visit: https://search.google.com/test/rich-results
Enter: https://uddeepta-deka.github.io/
```

### **Test Performance:**
```
Visit: https://pagespeed.web.dev/
Enter: https://uddeepta-deka.github.io/
```

### **Validate HTML:**
```
Visit: https://validator.w3.org/
Enter: https://uddeepta-deka.github.io/
```

---

## 🎯 **Common Mistakes to Avoid**

### **❌ Don't:**
```html
<!-- Missing alt text -->
<img src="photo.jpg">

<!-- Non-descriptive alt -->
<img src="photo.jpg" alt="image">

<!-- Missing ARIA label on icon-only button -->
<button><i class="fa-search"></i></button>

<!-- No loading attribute -->
<img src="large-image.jpg" alt="...">

<!-- Missing width/height (causes layout shift) -->
<img src="photo.jpg" alt="...">
```

### **✅ Do:**
```html
<!-- Descriptive alt text -->
<img src="photo.jpg" alt="Uddeepta Deka presenting at ICTS conference">

<!-- Icon with label -->
<button aria-label="Search">
    <i class="fa-search" aria-hidden="true"></i>
</button>

<!-- Lazy loading -->
<img src="large-image.jpg" alt="..." loading="lazy">

<!-- Prevent layout shift -->
<img src="photo.jpg" alt="..." width="800" height="600">
```

---

**Last Updated:** 2025
**For:** Uddeepta Deka Portfolio Site
**Compatibility:** GitHub Pages, Jekyll, Modern Browsers
