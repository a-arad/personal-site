# Personal Website — Design Doc

## Summary

A minimal, readable digital garden hosted on Neocities. Hand-written HTML, single shared CSS stylesheet, no build tools. Mixed content: technical notes and personal writing.

## Site Structure

```
site/
├── index.html              # Landing page — intro + garden entry list
├── about.html              # Who you are, what this site is
├── links.html              # Sites you like (low priority)
├── style.css               # Single shared stylesheet
├── garden/
│   ├── _template.html      # Skeleton for new posts
│   ├── my-first-post.html
│   └── ...
└── assets/
    └── (images, favicon, etc.)
```

- Every page includes the same stylesheet
- Nav block (`Home · Garden · About · Links`) copy-pasted into each page
- Garden posts are standalone complete HTML pages

## Visual Design

- **Typography-first.** System font stack, no external fonts.
- **Centered content column** ~650px max-width. Comfortable reading length.
- **Generous spacing.** ~1.6 line-height, breathing room between elements.
- **Black on off-white.** Distinct underlined links, maybe one muted accent color.
- **No decoration.** No hamburger menus, hero images, cards, or JS UI. Text and links.

### Navigation

Horizontal `<nav>` at the top: `Home · Garden · About · Links`. Simple separators.

### Garden Index (index.html)

- Short intro paragraph
- List of entries: title, date, optional one-line description
- Newest first

### Individual Garden Pages

- Title and date at top
- Content body
- "Back to garden" link at bottom

## Editing & Posting Workflow

1. Copy `garden/_template.html` to `garden/new-post.html`
2. Fill in title, date, body content
3. Add entry link to `index.html`
4. Deploy via `neocities push` CLI or browser dashboard

### Template File

Pre-filled skeleton with:
- `<head>` with stylesheet link and `<title>` placeholder
- Nav bar
- `<article>` with title/date/body placeholders
- Footer "back to garden" link

## Non-Goals

- No analytics, cookies, or tracking
- No build step or static site generator
- No RSS feed (can add later by hand if desired)
- No JavaScript required for core functionality
- Indie web integration (webrings, blogrolls) is not a priority
