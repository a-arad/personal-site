# Personal Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a minimal, readable digital garden as hand-written HTML + CSS, ready to deploy to Neocities.

**Architecture:** Static site with a single shared stylesheet. Every page is a standalone `.html` file with copy-pasted nav. Garden posts live in `garden/`. A `_template.html` skeleton makes creating new posts fast.

**Tech Stack:** HTML, CSS. No JS, no build tools. Neocities CLI for deployment.

---

### Task 1: Create the shared stylesheet (`style.css`)

**Files:**
- Create: `site/style.css`

**Step 1: Write `style.css`**

System font stack, centered content column, typography defaults, nav styling, article/post styling, link styles.

```css
/* === Reset === */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* === Base === */
html {
  font-size: 18px;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji";
  line-height: 1.6;
  color: #1a1a1a;
  background: #fafaf8;
  max-width: 650px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

/* === Typography === */
h1 {
  font-size: 1.6rem;
  margin-bottom: 0.5rem;
}

h2 {
  font-size: 1.3rem;
  margin-top: 2rem;
  margin-bottom: 0.5rem;
}

h3 {
  font-size: 1.1rem;
  margin-top: 1.5rem;
  margin-bottom: 0.4rem;
}

p {
  margin-bottom: 1rem;
}

/* === Links === */
a {
  color: #2c5f8a;
  text-decoration: underline;
  text-underline-offset: 2px;
}

a:hover {
  color: #1a3d5c;
}

/* === Nav === */
nav {
  margin-bottom: 2.5rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #ddd;
}

nav a {
  text-decoration: none;
  color: #1a1a1a;
  margin-right: 1.5rem;
}

nav a:hover {
  text-decoration: underline;
}

/* === Garden entry list === */
.garden-list {
  list-style: none;
  padding: 0;
}

.garden-list li {
  margin-bottom: 1rem;
}

.garden-list .date {
  color: #777;
  font-size: 0.85rem;
}

/* === Article (garden post) === */
article header {
  margin-bottom: 2rem;
}

article header .date {
  color: #777;
  font-size: 0.85rem;
}

article p,
article ul,
article ol,
article blockquote,
article pre {
  margin-bottom: 1rem;
}

article blockquote {
  border-left: 3px solid #ddd;
  padding-left: 1rem;
  color: #555;
}

article pre {
  background: #f0f0ee;
  padding: 1rem;
  overflow-x: auto;
  font-size: 0.85rem;
  border-radius: 4px;
}

article code {
  background: #f0f0ee;
  padding: 0.15rem 0.3rem;
  font-size: 0.85rem;
  border-radius: 3px;
}

article pre code {
  background: none;
  padding: 0;
}

/* === Footer === */
.back-link {
  margin-top: 3rem;
  padding-top: 1rem;
  border-top: 1px solid #ddd;
}

footer {
  margin-top: 3rem;
  padding-top: 1rem;
  border-top: 1px solid #ddd;
  color: #999;
  font-size: 0.8rem;
}
```

**Step 2: Verify**

Open in browser to confirm the stylesheet loads (will test properly with index.html in Task 2).

**Step 3: Commit**

```bash
git add site/style.css
git commit -m "add shared stylesheet: system fonts, 650px column, typography"
```

---

### Task 2: Create the landing page (`index.html`)

**Files:**
- Create: `site/index.html`

**Step 1: Write `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="A digital garden — technical notes and personal writing.">
  <title>Home</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/links.html">Links</a>
  </nav>

  <h1>Welcome</h1>
  <p>This is my digital garden. A place for technical notes, personal writing, and things I find interesting. It grows slowly.</p>

  <h2>Garden</h2>
  <ul class="garden-list">
    <li>
      <a href="garden/hello-world.html">Hello world</a>
      <span class="date">2026-02-22</span>
    </li>
  </ul>

  <footer>
    <p>Hand-built with HTML and CSS.</p>
  </footer>
</body>
</html>
```

**Step 2: Open `site/index.html` in browser**

Verify: nav renders horizontally, content is centered ~650px, typography looks clean, garden list entry shows title + date.

**Step 3: Commit**

```bash
git add site/index.html
git commit -m "add index.html: landing page with garden entry list"
```

---

### Task 3: Create the about page (`about.html`)

**Files:**
- Create: `site/about.html`

**Step 1: Write `about.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="About this site and its author.">
  <title>About</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/links.html">Links</a>
  </nav>

  <h1>About</h1>
  <p>This is a personal website. It's a digital garden where I write about things I'm learning, building, and thinking about.</p>
  <p>No algorithms, no tracking, no ads. Just HTML and CSS.</p>

  <footer>
    <p>Hand-built with HTML and CSS.</p>
  </footer>
</body>
</html>
```

**Step 2: Open in browser, verify nav links work between index and about**

**Step 3: Commit**

```bash
git add site/about.html
git commit -m "add about.html"
```

---

### Task 4: Create the links page (`links.html`)

**Files:**
- Create: `site/links.html`

**Step 1: Write `links.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="Sites I like.">
  <title>Links</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/links.html">Links</a>
  </nav>

  <h1>Links</h1>
  <p>Sites I enjoy visiting.</p>

  <ul>
    <li><a href="https://32bit.cafe">32-Bit Cafe</a> — community for personal web hobbyists</li>
  </ul>

  <footer>
    <p>Hand-built with HTML and CSS.</p>
  </footer>
</body>
</html>
```

**Step 2: Open in browser, verify all three nav links now work across all pages**

**Step 3: Commit**

```bash
git add site/links.html
git commit -m "add links.html"
```

---

### Task 5: Create the garden post template (`garden/_template.html`)

**Files:**
- Create: `site/garden/_template.html`

**Step 1: Write `_template.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="DESCRIPTION">
  <title>TITLE</title>
  <link rel="stylesheet" href="../style.css">
</head>
<body>
  <nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/links.html">Links</a>
  </nav>

  <article>
    <header>
      <h1>TITLE</h1>
      <span class="date">YYYY-MM-DD</span>
    </header>

    <p>Start writing here.</p>
  </article>

  <div class="back-link">
    <a href="/">← Back to garden</a>
  </div>
</body>
</html>
```

**Step 2: Commit**

```bash
git add site/garden/_template.html
git commit -m "add garden post template"
```

---

### Task 6: Create the first garden post (`garden/hello-world.html`)

**Files:**
- Create: `site/garden/hello-world.html` (copy from `_template.html`, fill in)

**Step 1: Copy template and fill in**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="First post in the garden.">
  <title>Hello world</title>
  <link rel="stylesheet" href="../style.css">
</head>
<body>
  <nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/links.html">Links</a>
  </nav>

  <article>
    <header>
      <h1>Hello world</h1>
      <span class="date">2026-02-22</span>
    </header>

    <p>This is the first entry in my digital garden. More to come.</p>
  </article>

  <div class="back-link">
    <a href="/">← Back to garden</a>
  </div>
</body>
</html>
```

**Step 2: Open in browser**

Verify: post renders cleanly, nav works, "back to garden" links to index, index links to this post.

**Step 3: Commit**

```bash
git add site/garden/hello-world.html
git commit -m "add first garden post: hello world"
```

---

### Task 7: Final verification and Neocities setup

**Step 1: Open `site/index.html` in browser, click through every link**

Verify all navigation works: Home → About → Links → Home → hello-world post → back to garden.

**Step 2: Install Neocities CLI (optional)**

```bash
gem install neocities
```

Or use the Neocities web dashboard at https://neocities.org to create an account and upload the `site/` directory contents.

**Step 3: Commit any final tweaks**

```bash
git add -A && git commit -m "ready for first deploy"
```
