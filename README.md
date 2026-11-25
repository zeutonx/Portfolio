# Abhinaash's Notebook

Personal site and blog of Abhinaash Tiwari — proof-oriented notes and long-form expository essays on mathematics, with a focus on optimization theory, optimal transport, and geometric deep learning.

**Live site:** [abhinaash.com.np](https://abhinaash.com.np)

## Overview

The site is plain HTML and CSS with no build step, hosted on GitHub Pages. Mathematics is typeset client-side with MathJax, so posts are written directly in HTML with LaTeX inside `$…$` and `$$…$$` delimiters.

The design is deliberately plain: white page, neutral greys, one blue accent, IBM Plex Sans for text and IBM Plex Mono for code and dates. Spacing, type sizes, colours and the corner radius are tokens at the top of `style.css`; use those rather than new values.

## Posts

| Post | File |
|---|---|
| Long Short-Term Memory, from First Principles | `posts/lstm.html` |
| Singular Value Decomposition: Finding the Hidden Geometry Inside a Matrix | `posts/svd.html` |
| Convolution: The Mathematics Behind Sliding, Smoothing, and Pattern Matching | `posts/convolution.html` |
| Geometric Deep Learning, Explained: Why Symmetry Is the Real Architecture | `posts/geometric-deep-learning.html` |

## Project structure

```
.
├── index.html                  Home: featured post + recent posts
├── about.html                  Bio
├── posts.html                  Full post index
├── resume.html                 Academic CV
├── posts/
│   └── <post>.html             One file per blog post
├── assets/
│   ├── css/
│   │   ├── style.css           Global theme: colours, fonts, layout, header, footer
│   │   ├── post.css            Shared styles for long-form posts (TOC, math, tables, notes, code, figures)
│   │   ├── article.css         Post cards on the home and posts pages
│   │   └── about.css           About page
│   └── images/
│       └── profile.png
└── CNAME                       Custom domain for GitHub Pages
```

## Adding a post

1. Copy an existing post (e.g. `posts/svd.html`) to `posts/<slug>.html` and replace the content. Keep the `<head>` — it loads the fonts, links `style.css` and `post.css`, and configures MathJax — but update everything page-specific in it: `<title>`, the description, the canonical URL, the `og:`/`twitter:` tags, and the JSON-LD block (headline, description, `datePublished`, URLs). Add the new URL to `sitemap.xml` too.
2. Write maths as LaTeX. Inline: `$A = U\Sigma V^T$`. Display: wrap in `<div class="_math-block">$$ … $$</div>` so wide equations scroll instead of overflowing on narrow screens.
3. Escape HTML-sensitive characters inside maths: use `&lt;` and `&gt;` for `<` and `>`, and `&amp;` for the `&` alignment character in `aligned` environments.
4. Available building blocks (all in `post.css`):
   - `._toc` — table of contents box; link each entry to a section `id`
   - `._secondary-title` (`<h2>`) / `._tertiary-title` (`<h3>`) — numbered sections and subsections; the post title is the page's only `<h1>`
   - `._note` with a `._note-label` — shaded note for caveats and technical asides
   - `._table-wrap` around a `<table>` — ruled table
   - `._list` — spaced list
5. Add a card for the post at the top of `posts.html`, and update the featured/recent cards in `index.html`.

## Running locally

Any static file server works. With Python:

```bash
python -m http.server 8123
```

Then open `http://localhost:8123`. Serving over HTTP (rather than opening the files directly) is needed for the stylesheets and MathJax to load with the relative paths used in the pages.

## Deployment

Pushing to `main` deploys automatically via GitHub Pages. The `CNAME` file maps the site to the custom domain.

## Credits and licence

Built on a blog template by westtle, used under the MIT licence — see `LICENSE.md`. Post content © Abhinaash Tiwari.
