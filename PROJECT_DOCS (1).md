# 📘 Project Documentation
## DecodeLabs — Frontend Development Project 1
### Static Webpage Design | Batch 2026

---

## Table of Contents

1. [Project Brief](#1-project-brief)
2. [Learning Objectives](#2-learning-objectives)
3. [File Structure Explained](#3-file-structure-explained)
4. [HTML Documentation](#4-html-documentation)
5. [CSS Documentation](#5-css-documentation)
6. [Layout System](#6-layout-system)
7. [Design Decisions](#7-design-decisions)
8. [Accessibility Standards](#8-accessibility-standards)
9. [Quality Checklist](#9-quality-checklist)
10. [Key Concepts Learned](#10-key-concepts-learned)

---

## 1. Project Brief

**Project Name:** Static Webpage Design  
**Project Number:** Project 1  
**Program:** DecodeLabs Industrial Training — Batch 2026  
**Track:** Frontend Development  
**Difficulty:** Beginner  
**Skills Required:** HTML fundamentals, CSS styling  

### Goal
Create a static personal portfolio webpage using only HTML and CSS, demonstrating mastery of semantic structure, clean layout, and the fundamental relationship between content and style.

### Why This Project Matters
Before building dynamic, data-driven applications, a developer must understand the structural phase. This project proves the ability to craft a clean, readable layout through pure markup and styling logic — the foundation of every interface users will ever see.

---

## 2. Learning Objectives

By completing this project, the following skills are demonstrated:

### HTML Skills
- Writing a valid HTML5 document with proper `<!DOCTYPE>`, `<html>`, `<head>`, and `<body>`
- Using semantic landmark elements (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- Applying correct heading hierarchy (one `<h1>`, then `<h2>`, then `<h3>` — never skipping levels)
- Adding images with `alt` attributes and explicit `width`/`height` dimensions
- Creating navigation with `<nav>` and anchor `<a>` links

### CSS Skills
- Linking an external stylesheet using `<link rel="stylesheet">`
- Using CSS Custom Properties (variables) for consistent design tokens
- Building layouts with CSS Grid (2D, for page structure)
- Aligning components with Flexbox (1D, for nav, cards, footer)
- Applying the DRY (Don't Repeat Yourself) principle with reusable classes
- Using BEM (Block__Element--Modifier) naming convention
- Writing hover effects and smooth transitions

### Design Skills
- Creating a clear visual hierarchy with typography and spacing
- Choosing a consistent color palette
- Making a layout that is clean and readable

---

## 3. File Structure Explained

```
project-1/
│
├── index.html          ← All page content and structure
├── style.css           ← All visual styling (no inline styles!)
├── README.md           ← Quick-start guide for the project
└── PROJECT_DOCS.md     ← This file — full technical documentation
```

### Why Two Separate Files?

This is called **Separation of Concerns** — one of the most important rules in web development.

- `index.html` only describes **what** the content is (structure)
- `style.css` only describes **how** it looks (appearance)

If you ever need to change a color or font, you change it in ONE place (`style.css`) and it updates everywhere. This is far better than repeating styles in every HTML element.

---

## 4. HTML Documentation

### 4.1 Document Structure

```html
<!DOCTYPE html>           ← Tells browser this is HTML5
<html lang="en">          ← Language attribute (good for accessibility)
<head>
  <meta charset="UTF-8">         ← Supports all characters
  <meta name="viewport" ...>     ← Makes page work on mobile
  <title>...</title>             ← Tab title in browser
  <link rel="stylesheet" ...>    ← Links external CSS file
  <link ... Google Fonts>        ← Loads web fonts
</head>
<body>
  <header>...</header>           ← Top navigation
  <main>                         ← All page content
    <section>...</section>       ← Each content block
  </main>
  <footer>...</footer>           ← Bottom of page
</body>
</html>
```

### 4.2 Semantic Tags Used

| Tag | Purpose | Where Used |
|---|---|---|
| `<header>` | Page or section header | Top navigation area |
| `<nav>` | Navigation links | Inside header + footer |
| `<main>` | Primary page content | Wraps all sections |
| `<section>` | Thematic content group | Hero, About, Skills, Projects, Contact |
| `<article>` | Self-contained content | Skill cards, Project cards |
| `<footer>` | Page footer | Bottom of page |
| `<h1>` | Main page heading (ONE only) | Hero section title |
| `<h2>` | Section headings | About, Skills, Projects, Contact titles |
| `<h3>` | Sub-headings | Card titles, contact labels |
| `<img>` | Images | Hero, About, Skills, Projects, Contact |
| `<a>` | Links | Navigation, buttons |
| `<ul>` / `<li>` | Navigation lists | Nav links |

### 4.3 The ONE `<h1>` Rule

Every page must have exactly **one** `<h1>`. Think of it as the title of a book — there is only one title per book.

```html
<!-- ✅ CORRECT — only one h1 on the whole page -->
<h1 class="hero__title">Hi, I'm a Frontend Developer 👋</h1>

<!-- Then h2 for each major section -->
<h2 class="section__title">About Me</h2>
<h2 class="section__title">My Skills</h2>

<!-- Then h3 inside sections -->
<h3 class="skill-card__title">HTML5</h3>
```

### 4.4 Image Best Practices

Every `<img>` tag in this project follows three rules:

```html
<img
  src="path/to/image.jpg"
  alt="Description of the image for screen readers"
  width="500"
  height="400"
/>
```

- `alt` — describes the image for users who cannot see it (required for accessibility)
- `width` and `height` — tells the browser how much space to reserve before the image loads, preventing layout shift (CLS)

---

## 5. CSS Documentation

### 5.1 CSS Variables (Design Tokens)

At the top of `style.css`, all design values are stored as variables inside `:root`. This means you only need to change ONE value to update it everywhere.

```css
:root {
  --color-primary:   #2563eb;   /* Main blue color */
  --color-dark:      #1e293b;   /* Headings */
  --color-text:      #475569;   /* Body text */
  --font-heading:    'Poppins', sans-serif;
  --spacing-md:      2rem;
  --border-radius:   12px;
}
```

To change the primary color of the whole site, you only edit `--color-primary` here.

### 5.2 BEM Naming Convention

BEM stands for **Block__Element--Modifier**. It is a way of naming CSS classes so they are easy to understand and never conflict with each other.

```
.block              ← The component itself
.block__element     ← A part inside the component
.block--modifier    ← A variation of the component
```

**Examples from this project:**

```css
/* Block */
.skill-card { }

/* Element — part of the skill card */
.skill-card__title { }
.skill-card__icon { }
.skill-card__description { }

/* Modifier — a different version of the block */
.project-card--featured { }
.project-card__tag--locked { }

/* Button block + modifier */
.btn { }            /* Base button styles */
.btn--primary { }   /* Blue filled button */
```

### 5.3 DRY Principle in CSS

DRY = **Don't Repeat Yourself**. Instead of writing the same styles many times, you write them once and reuse them.

**Without DRY (bad):**
```css
.hero-heading { font-family: 'Poppins'; font-size: 2.2rem; color: #1e293b; }
.about-heading { font-family: 'Poppins'; font-size: 2.2rem; color: #1e293b; }
.skills-heading { font-family: 'Poppins'; font-size: 2.2rem; color: #1e293b; }
```

**With DRY (good — used in this project):**
```css
.section__title {
  font-family: var(--font-heading);
  font-size: 2.2rem;
  color: var(--color-dark);
  text-align: center;
}
```
Then in HTML: `<h2 class="section__title">About Me</h2>` — works for every section.

---

## 6. Layout System

### 6.1 CSS Grid — For Page Structure (2D)

CSS Grid is used for any layout that has both **rows and columns**. It controls the big picture of the page.

**Hero Section — 2 equal columns:**
```css
.hero {
  display: grid;
  grid-template-columns: 1fr 1fr;  /* Two equal columns */
  gap: 4rem;
}
```

**Skills Section — 4 cards in a row:**
```css
.skills__grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);  /* Four equal columns */
  gap: 2rem;
}
```

**Projects Section — Featured card spans full width:**
```css
.projects__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.project-card--featured {
  grid-column: 1 / -1;  /* Span ALL columns */
}
```

### 6.2 Flexbox — For Component Alignment (1D)

Flexbox is used when items need to be aligned in **one direction** (row or column).

**Navigation bar — logo left, links right:**
```css
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;  /* Space between logo and links */
}
```

**Nav links — items in a horizontal row:**
```css
.nav__links {
  display: flex;
  gap: 2rem;
}
```

**Contact items — icon + text side by side:**
```css
.contact__item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}
```

### 6.3 When to Use Grid vs Flexbox

| Use Grid When... | Use Flexbox When... |
|---|---|
| Layout has rows AND columns | Items are in ONE row or ONE column |
| Designing the overall page structure | Aligning items inside a component |
| Cards in a multi-column grid | Navigation links in a row |
| Complex 2D arrangements | Centering a single item |

---

## 7. Design Decisions

### 7.1 Color Palette

| Color Name | Hex Code | Used For |
|---|---|---|
| Primary Blue | `#2563eb` | Buttons, logo, links, accents |
| Secondary Green | `#10b981` | Success/active states |
| Dark Navy | `#1e293b` | Headings and important text |
| Slate | `#475569` | Body paragraph text |
| Off-White | `#f8fafc` | Page background, section backgrounds |
| White | `#ffffff` | Card backgrounds, header |

**Why these colors?** Blue conveys trust and professionalism (common in tech portfolios). The dark navy on light background gives a contrast ratio well above the 4.5:1 accessibility requirement.

### 7.2 Typography

| Role | Font | Weight |
|---|---|---|
| Headings, Logo, Nav | Poppins | 600, 700 |
| Body text, Paragraphs | Roboto | 400, 500 |

**Why two fonts?** A heading font and a body font create visual hierarchy. Poppins is geometric and modern for headings. Roboto is highly readable for long text.

### 7.3 Spacing Scale

All spacing in the project uses a consistent scale via CSS variables:

| Variable | Value | Used For |
|---|---|---|
| `--spacing-xs` | 0.5rem (8px) | Small gaps, margins |
| `--spacing-sm` | 1rem (16px) | Inside cards, between items |
| `--spacing-md` | 2rem (32px) | Between sections (small) |
| `--spacing-lg` | 4rem (64px) | Between major sections |
| `--spacing-xl` | 6rem (96px) | Hero top/bottom padding |

Using a scale (instead of random values like 13px, 27px) keeps the design consistent and professional.

---

## 8. Accessibility Standards (A11Y)

Accessibility means building webpages that everyone can use, including people who use screen readers or keyboard navigation.

### What Was Done for Accessibility

**Alt text on all images:**
```html
<img
  src="image.jpg"
  alt="A laptop showing code on screen representing frontend development"
/>
```

**Semantic landmarks** let screen readers jump between sections:
- `<header>` — screen reader announces "banner"
- `<nav>` — screen reader announces "navigation"
- `<main>` — screen reader announces "main content"
- `<footer>` — screen reader announces "content info"

**`lang` attribute** on `<html>` tells screen readers which language to use:
```html
<html lang="en">
```

**Footer nav has `aria-label`** to distinguish it from the header nav:
```html
<nav class="footer__nav" aria-label="Footer navigation">
```

**Color contrast** — the text color `#475569` on background `#f8fafc` gives a contrast ratio of approximately 5.9:1, which passes the WCAG AA standard (minimum 4.5:1).

---

## 9. Quality Checklist

Before submitting, verify every item below:

### HTML Quality
- [ ] `<!DOCTYPE html>` is the very first line
- [ ] `<html lang="en">` has a language attribute
- [ ] `<meta charset="UTF-8">` is in the `<head>`
- [ ] `<meta name="viewport">` is in the `<head>`
- [ ] `<title>` is present and descriptive
- [ ] CSS is linked with `<link>` — not `<style>` or `style=""` attributes
- [ ] Only ONE `<h1>` exists on the entire page
- [ ] Headings go h1 → h2 → h3 with no levels skipped
- [ ] Every `<img>` has an `alt` attribute
- [ ] Every `<img>` has `width` and `height` attributes
- [ ] Semantic tags are used (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)

### CSS Quality
- [ ] No inline styles anywhere in the HTML (no `style=""` attributes)
- [ ] No `<style>` blocks inside HTML — all CSS is in `style.css`
- [ ] CSS Variables are defined in `:root`
- [ ] BEM naming is used consistently
- [ ] CSS Grid is used for at least one layout
- [ ] Flexbox is used for at least one component
- [ ] Class names are descriptive and meaningful

### Visual Quality
- [ ] All sections are visible and readable
- [ ] Images load correctly
- [ ] Navigation links work (scroll to sections)
- [ ] Font loads from Google Fonts
- [ ] Cards have visible spacing between them
- [ ] The page looks good from top to bottom

---

## 10. Key Concepts Learned

### Information Architecture (IA)
Plan the structure before writing code. Know what sections you need and how they connect — like a map of the page.

### Semantic HTML
Use tags that describe the meaning of content, not just its appearance. `<nav>` means navigation. `<article>` means a self-contained piece of content. This helps browsers, search engines, and screen readers understand the page.

### Separation of Concerns
HTML = content and structure. CSS = visual appearance. Keep them separate so each file has one job and is easy to maintain.

### The CSS Box Model
Every HTML element is a box with: **content → padding → border → margin**. Understanding this is how you control spacing and layout.

### CSS Grid vs Flexbox
Grid handles two-dimensional layouts (rows AND columns). Flexbox handles one-dimensional alignment (a row OR a column). Use the right tool for the right job.

### DRY Principle
Write a style once, use it many times. If you find yourself writing the same CSS in multiple places, create a reusable class instead.

### Accessibility
The web should work for everyone. Add `alt` text, use semantic tags, maintain color contrast, and structure headings correctly. This is not optional — it is professional standard.

---

## 📬 DecodeLabs

- 📞 +91 89330 06408
- ✉️ decodelabs.tech@gmail.com
- 🌐 www.decodelabs.tech
- 📍 Greater Lucknow, India

---

*Documentation written for DecodeLabs Batch 2026 — Frontend Development Track, Project 1.*
