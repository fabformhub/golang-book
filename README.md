# The Golang Book

A modern, developer‑friendly introduction to the Go programming language. This project powers the website at **https://golang-book.vercel.app**, presenting the book as a clean, fast, fully responsive reading experience built with Astro and MDX.

The book is structured as a series of chapters, examples, and explanations designed to help developers learn Go from first principles. The site is optimized for long‑form reading, clear navigation, and fast performance.

---

## Project Overview

The Golang Book website is built using:

- **Astro 6** for a fast, content‑focused architecture
- **MDX** for rich, interactive chapters
- **Tailwind CSS** for styling
- **Fuse.js** for instant client‑side search
- **Bookworm Light** as the base reading theme

The project is fully static and deploys cleanly to any modern hosting platform, including Vercel, Netlify, Cloudflare Pages, and GitHub Pages.

---

## Features

- Clean, distraction‑free reading layout
- Chapter‑based navigation
- Search across all chapters
- Syntax‑highlighted Go code examples
- Fully responsive design
- SEO‑optimized metadata
- Fast builds and instant page loads
- Easy to extend with new chapters or sections

---

## Live Site

The book is published at:

**https://golang-book.vercel.app**

---

## Getting Started

Clone the repository:

```bash
git clone https://github.com/fabformhub/golang-book
cd golang-book
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

The site will reload automatically as you edit chapters or components.

---

## Writing Chapters

Chapters are written in **Markdown or MDX** and stored in the project’s content directories. Each chapter supports:

- Headings
- Code blocks
- Callouts
- Tables
- Embedded components
- Images

To add a new chapter, create a new `.md` or `.mdx` file and update the navigation in `menu.json`.

---

## Deployment

Build the production site:

```bash
npm run build
```

Deploy the generated `dist/` folder to your hosting provider of choice. The project is optimized for static hosting and requires no backend.

---

## Credits

This project uses the **Bookworm Light Astro** theme as a foundation, with customizations and improvements by **Fabform** to support long‑form technical writing.

---

## License

Released under the MIT License.

