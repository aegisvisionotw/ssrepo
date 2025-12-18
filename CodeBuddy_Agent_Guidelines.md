# CodeBuddy Agent Guidelines

This document outlines the standard operating procedures and check points for CodeBuddy agents when working on web development projects.

## 🎯 Core Responsibilities

As a CodeBuddy agent, your primary goal is to ensure high-quality, modern, and responsive web applications that provide excellent user experience across all devices.

## ✅ Standard Check Points

### 1. Modern Responsive Design & Centered Content

#### ✅ Style Requirements
- [ ] **Modern UI Framework**: Use modern CSS frameworks (Tailwind CSS, Bootstrap 5, or custom modern CSS)
- [ ] **Responsive Design**: Ensure pages work perfectly on:
  - PC/Desktop (≥1024px)
  - Tablet (768px-1023px) 
  - Mobile (≤767px)
- [ ] **Content Centering**: All page content must be centered:
  - **Vertical**: `justify-content: center` for flexbox
  - **Horizontal**: `align-items: center` for flexbox
  - **Text**: `text-align: center` for inline elements
- [ ] **Modern Design Elements**:
  - Smooth transitions and hover effects
  - Card-based layouts where appropriate
  - Proper spacing and typography
  - Modern color schemes with gradients
  - Backdrop filters and glass-morphism effects

#### ✅ Mobile Optimization
- [ ] Touch-friendly button sizes (minimum 44px)
- [ ] Readable font sizes on mobile
- [ ] Proper viewport meta tag
- [ ] Collapsible navigation on mobile
- [ ] Optimized images and assets

#### ✅ CSS Architecture
- [ ] CSS variables for consistent theming
- [ ] Mobile-first approach
- [ ] Semantic HTML5 structure
- [ ] Accessibility considerations (ARIA labels, semantic tags)

### 2. Path & Link Validation

#### ✅ Internal Links
- [ ] **Absolute Path Verification**: All internal links use correct absolute paths
- [ ] **File Existence Check**: Verify all referenced files exist:
  - `/footer.html` - Common footer template
  - `/home.html` - Main homepage
  - `/login.html` - Login page
  - `/tools/calculator.html` - Calculator tool
  - `/fe/buffettletters/buffettletters.html` - Buffett letters
  - `/fe/tax/cn/personalIncomeTaxCN.html` - Personal income tax
- [ ] **Consistent URL Structure**: Use consistent path patterns
- [ ] **Case Sensitivity**: Ensure case matches actual file names

#### ✅ External Resources
- [ ] **CDN Links**: Verify all CDN links are working and use HTTPS
- [ ] **Fallback Options**: Provide fallbacks for external resources
- [ ] **CORS Considerations**: Ensure external resources allow cross-origin requests

#### ✅ Navigation Flow
- [ ] **Breadcrumb Navigation**: Implement where appropriate
- [ ] **Back to Home**: Ensure users can navigate back to homepage
- [ ] **Footer Links**: Verify footer navigation works correctly
- [ ] **404 Handling**: Handle broken links gracefully

## 🚀 Implementation Standards

### File Structure
```
/workspace/
├── home.html                 # Main homepage
├── login.html               # Login page
├── footer.html              # Footer template
├── tools/
│   └── calculator.html      # Calculator tool
└── fe/
    ├── buffettletters/
    │   └── buffettletters.html
    └── tax/
        └── cn/
            └── personalIncomeTaxCN.html
```

### CSS Standards
```css
/* Modern responsive body */
body {
    display: flex;
    flex-direction: column;
    justify-content: center;    /* Vertical centering */
    align-items: center;        /* Horizontal centering */
    min-height: 100vh;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

/* Centered container */
.container {
    margin: auto;
    text-align: center;
    max-width: 1200px;
    padding: 2rem;
}
```

## 🔍 Quality Assurance Checklist

### Pre-Deployment Checks
- [ ] **Cross-browser Testing**: Chrome, Firefox, Safari, Edge
- [ ] **Device Testing**: iPhone, Android, Tablet, Desktop
- [ ] **Performance Check**: Page load time < 3 seconds
- [ ] **Accessibility**: WCAG 2.1 AA compliance
- [ ] **SEO Meta Tags**: Title, description, meta tags present
- [ ] **Error Handling**: Graceful degradation for JS failures

### Code Quality
- [ ] **Valid HTML5**: Pass W3C validation
- [ ] **Semantic HTML**: Proper use of header, nav, main, section, footer
- [ ] **CSS Organization**: Logical structure, comments, and organization
- [ ] **JavaScript Best Practices**: Modern ES6+, error handling, no console errors

## 📱 Responsive Testing Matrix

| Device Width | Breakpoint | Checks Required |
|-------------|------------|-----------------|
| 320px-767px | Mobile | Touch targets, font size, layout collapse |
| 768px-1023px | Tablet | Medium layout adjustments |
| 1024px+ | Desktop | Full layout, hover states |

## 🎨 Design System Guidelines

### Color Palette
- Primary: #667eea, #764ba2 (gradient)
- Secondary: #f8fafc, #ffffff
- Accent: #10b981, #ef4444, #f59e0b
- Text: #1f2937, #6b7280

### Typography
- Headings: 1.75rem - 2.5rem
- Body: 1rem (16px minimum on mobile)
- Small text: 0.875rem (avoid where possible)

### Spacing
- Mobile: 0.5rem - 1.5rem
- Desktop: 1rem - 2rem
- Consistent 8px grid system

## 🔄 Maintenance Guidelines

### Regular Checks
- [ ] **Link Validation**: Check all internal/external links monthly
- [ ] **Performance Monitoring**: Page speed and Core Web Vitals
- [ ] **Browser Compatibility**: Test on new browser versions
- [ ] **User Feedback**: Monitor and address user issues

### Update Procedures
1. **Backup Current Version**: Create backup before major changes
2. **Test in Staging**: Validate changes in development environment
3. **Cross-Device Test**: Verify on all target devices
4. **Deploy**: Push changes to production
5. **Monitor**: Watch for issues post-deployment

## 🦶 Footer Integration Pattern

### Standard Footer Implementation
All pages should include a dynamically loaded footer using the following pattern:

#### HTML Structure
```html
<div id="footer-container"></div>
```

#### JavaScript Implementation
```javascript
// Include footer template
fetch('/footer.html')
    .then(response => response.text())
    .then(data => {
        const footerContainer = document.getElementById('footer-container');
        if (footerContainer) {
            footerContainer.innerHTML = data;
            footerContainer.style.textAlign = 'center';
            footerContainer.style.padding = '20px';
            footerContainer.style.marginTop = 'auto';
        }
    })
    .catch(error => console.error('Error loading footer:', error));
```

#### Alternative Implementation (for pages without pre-existing container)
```javascript
// Include footer template
fetch('/footer.html')
    .then(response => response.text())
    .then(data => {
        const footerContainer = document.createElement('div');
        footerContainer.innerHTML = data;
        footerContainer.style.textAlign = 'center';
        footerContainer.style.padding = '20px';
        footerContainer.style.marginTop = 'auto';
        document.body.appendChild(footerContainer);
    })
    .catch(error => console.error('Error loading footer:', error));
```

### Footer Integration Checklist
- [ ] **Footer Container**: Add `<div id="footer-container"></div>` to HTML
- [ ] **Fetch Script**: Include footer loading JavaScript in page script
- [ ] **Error Handling**: Ensure proper error handling for failed footer loads
- [ ] **Styling**: Apply consistent styling (center, padding, margin)
- [ ] **Path Verification**: Confirm `/footer.html` path is correct
- [ ] **Cross-browser Test**: Verify footer loads correctly in all browsers

### Implementation Notes
- Place the footer container at the end of the `<body>` tag
- Load footer asynchronously to prevent blocking page rendering
- Apply consistent styling to match page design
- Handle errors gracefully with console logging
- Use absolute paths for footer file reference

## 📋 Reporting Template

When making changes, include this checklist in your commit message:

```
✅ Responsive Design: Mobile/Tablet/Desktop tested
✅ Content Centering: Vertical/Horizontal/Text alignment verified  
✅ Path Validation: All links and references checked
✅ Browser Compatibility: Chrome/Firefox/Safari tested
✅ Performance: Page load time optimized
```

---

**Version**: 1.0  
**Last Updated**: 2025-12-17  
**Maintainer**: CodeBuddy Agent Team