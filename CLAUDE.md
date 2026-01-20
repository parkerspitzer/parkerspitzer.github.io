# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static single-page website for Dakota Lock & Key, a locksmith business serving Vermillion, SD and surrounding areas. The site is hosted on GitHub Pages at www.dakotalockandkey.com.

## Repository Structure

All website files are in the root directory:
- `index.html` - Single-page application with all sections (#services, #about, #reviews, #contact, #service-areas)
- `styles.css` - All styling using CSS custom properties for theming
- `script.js` - Mobile menu, smooth scrolling, and navbar scroll behavior
- `images/` - AAA logo SVG and social media preview image
- `CNAME` - Custom domain configuration for GitHub Pages
- `sitemap.xml` - SEO sitemap (update lastmod when making content changes)
- `robots.txt` - Search engine crawling rules

## Development Workflow

**Local Testing**:
```bash
# Open directly in browser
open index.html

# Or run local server
python3 -m http.server 8000
# Then visit http://localhost:8000
```

**Deployment**:
```bash
# Changes pushed to main branch automatically deploy to www.dakotalockandkey.com
git add .
git commit -m "Description of changes"
git push origin main
```

## Architecture

**Single-Page Design**: All content lives in one HTML file. Navigation uses anchor links (#services, #about, etc.) with smooth scrolling JavaScript. The navbar uses scroll-based hide/show behavior.

**SEO-Heavy Implementation**: The site is optimized for local locksmith searches:
- Extensive meta tags in `<head>` (Open Graph, Twitter Cards)
- JSON-LD structured data for LocalBusiness (lines 35-110)
- Individual Review schemas for each customer testimonial (lines 113-175)
- Keywords target "vehicle lockout", "residential locksmith", "Vermillion locksmith"
- Google Analytics 4 tracking: G-891Q39SS7E

**CSS Theming**: Uses CSS custom properties in `:root`:
- `--primary-color: #1a237e` (dark blue)
- `--secondary-color: #0d47a1` (lighter blue)
- `--accent-color: #ffc107` (yellow/gold)
- Mobile-first responsive design with breakpoints at 768px and 480px

**JavaScript Functionality**:
- Mobile hamburger menu toggle with click-outside-to-close
- Smooth scrolling for all anchor links
- Navbar scroll behavior (hides on scroll down, shows on scroll up)

## Business Information

- Phone: 605-624-6677
- Email: dakotalockandkey@gmail.com
- Location: Vermillion, SD
- Service Area: 40-mile radius including Yankton, Viborg, Centerville, Elk Point, Wakonda, Volin, Gayville
- Owner/Technician: Jeff Jensen
- AAA Approved service provider
- 24/7 emergency locksmith services

## Common Modifications

**Updating Contact Info**: Phone number appears in multiple places - search for "605-624-6677" across index.html to find all instances (typically 3-4 locations).

**Adding/Editing Services**: Service cards are in `<section id="services">` with class `.service-card`. Each contains an h3, descriptive paragraph, and bulleted list with class `.service-list`.

**Modifying Color Scheme**: Update CSS custom properties in `:root` selector (styles.css:2-10). Changes cascade throughout the entire site.

**Updating Structured Data**: JSON-LD schemas are in `<script type="application/ld+json">` tags in index.html head:
- LocalBusiness schema: lines 35-110 (update business info, service area, hours)
- Review schemas: lines 113-175 (add/update customer reviews with matching visible content)
- Keep aggregateRating in sync with actual reviews displayed

**Managing Reviews**: Reviews appear twice:
1. JSON-LD structured data (lines 113-175) for search engines
2. Visible review cards in `<section id="reviews">` (lines 320-348)
Keep both in sync when adding/removing reviews.

**Service Areas**: Service area cards are in `<section id="service-areas">` with class `.area-card`. Each highlights a specific town/region with SEO-optimized copy.

**Sitemap Updates**: When making significant content changes, update the `<lastmod>` date in sitemap.xml to current date in YYYY-MM-DD format.
