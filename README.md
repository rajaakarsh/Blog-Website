# Aakarsh's Blogs

![HTML5](https://img.shields.io/badge/HTML5-%23E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-%231572B6?logo=css3&logoColor=white) ![License](https://img.shields.io/badge/License-MIT-brightgreen) ![Stars](https://img.shields.io/github/stars/imaakarsh/Blog-Website?style=social) ![Issues](https://img.shields.io/github/issues/imaakarsh/Blog-Website)

A clean, responsive, fully static blog-website UI front-end prototype built with HTML5 and CSS3. It displays a collection of blog posts in a modern card-driven grid using CSS Grid and Flexbox, featuring card-based UI patterns and hover animations without JavaScript. This project provides a foundation for a future full-stack blog application.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Development](#development)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)
- [Author](#author)

## Features

| Feature | Description | Status |
|---|---|---|
| Fully responsive grid | CSS Grid + media queries adapt to any viewport | Stable |
| Image hover zoom | Subtle scale transform on hover for featured images | Stable |
| Card-based design | Consistent UI pattern for each blog entry | Stable |
| Author avatar | Dynamic avatar generated from DiceBear API | Stable |
| Category tags | Color-coded tags for quick content filtering | Stable |
| Clean code structure | Semantic HTML, BEM-style CSS naming | Stable |
| Refactored body & container styles | Background color and centered container layout for a cleaner appearance | Stable |
| Dark-mode placeholder | CSS variables prepared for future dark theme | Planned |

Each blog card in the UI displays:
- Featured image (sourced from Picsum Photos)
- Blog title and short description
- Author avatar (generated via DiceBear API)
- Category tag

## Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Markup | HTML5 | Semantic page structure |
| Styling | CSS3 (Grid, Flexbox, Variables) | Layout, responsiveness, theming |
| Images | Picsum Photos | Random placeholder images |
| Avatars | DiceBear API | Dynamic author avatars |
| Hosting (optional) | GitHub Pages | Free static site deployment |

## Project Structure

```
Blog-Website/
├── index.html          # Main entry point – static HTML page
├── style.css           # Global stylesheet (Grid, Flexbox, utilities)
├── image.png           # Project logo / banner (used in README)
└── README.md           # Documentation
```

The application uses a single-page static architecture where the browser loads `index.html` and `style.css`, rendering the UI entirely on the client side. All image assets are loaded from external services; no local images or scripts are required.

## Prerequisites

- A modern web browser (Chrome, Firefox, Edge, Safari)
- Optional: A local HTTP server (Python, Node.js, or Docker)

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/imaakarsh/Blog-Website.git
   cd Blog-Website
   ```

2. Open the site using one of the following methods:

   **Option A: Direct file open**
   
   Double-click `index.html` or open it via `file://` in your web browser.

   **Option B: Local HTTP server**

   Using Python:
   ```bash
   python -m http.server 8000
   ```

   Using Node:
   ```bash
   npx serve .
   ```

   Using Docker:
   ```bash
   docker run -v "$PWD":/usr/share/nginx/html:ro -p 8080:80 nginx
   ```

3. Navigate to `http://localhost:8000` (or the appropriate port configured by your server).

## Usage

### Common Tasks

| Scenario | Action |
|---|---|
| View the homepage | Open `index.html` in a web browser. |
| Test responsiveness | Resize the viewport or open DevTools → Device Toolbar. |
| Replace placeholder images | Edit the `src` attribute of `<img>` tags in `index.html`. |
| Change author avatars | Update the `src` URL of the avatar image (DiceBear API) with a different seed or style. |
| Add a new blog card | Copy an existing `<article class="card">` block, modify its content, and insert it into `<section class="grid">`. |

### Example Card Markup

```html
<article class="card">
  <img src="https://picsum.photos/seed/new/400/250" alt="New blog image" class="card__image" />
  <div class="card__content">
    <h2 class="card__title">My New Blog Post</h2>
    <p class="card__excerpt">
      A short description of the new post goes here. Keep it under 150 characters.
    </p>
    <div class="card__meta">
      <img src="https://api.dicebear.com/6.x/identicon/svg?seed=newauthor" alt="Author avatar" class="card__avatar" />
      <span class="card__author">New Author</span>
      <span class="card__tag">Tech</span>
    </div>
  </div>
</article>
```

## Development

### Setup

1. **Code Editor**: Use any editor with HTML/CSS linting support (e.g., VS Code, Sublime Text).
2. **Live Reload**: Use the VS Code extension *Live Server* or run `npx serve` for instant browser refresh on file changes.

### Code Style Guidelines

- **HTML**: Use semantic tags (`<section>`, `<article>`, `<header>`, `<footer>`).
- **CSS**: Follow BEM naming conventions (`block__element--modifier`). Keep selectors specific and avoid deep nesting.
- **Indentation**: 2 spaces (no tabs).
- **Comments**: Use `/* comment */` in CSS and `<!-- comment -->` sparingly in HTML.

### Recent CSS Refactor

- **Body background**: Uses the CSS variable `--bg-color` for theming.
- **Text color**: Managed via the variable `--text-color`.
- **Container layout**: Uses Flexbox centering for vertical alignment on tall viewports.
- **Container background**: Added variable `--container-bg` for theming.

```css
/* style.css – excerpt */
:root {
  --bg-color:      #f9fafb;   /* Light gray page background */
  --text-color:    #111111;   /* Primary text color */
  --container-bg: #ffffff;   /* Default container background */
}

/* Body */
body {
  margin: 0;
  font-family: system-ui, sans-serif;
  background-color: var(--bg-color);
  color: var(--text-color);
  display: flex;
  justify-content: center;
  align-items: flex-start;      /* Top‑aligned but centered horizontally */
}

/* Main container */
.container {
  max-width: 1200px;
  width: 100%;
  padding: 1rem;
  background-color: var(--container-bg);
  border-radius: 0.5rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}
```

### Testing

The project does not contain automated tests. Perform visual regression testing by opening the page across multiple browsers to verify layout consistency.

## Deployment

Because the site is static, deployment requires no build step.

### GitHub Pages

1. Push the repository to GitHub.
2. In the repository settings, select **Pages**.
3. Set **Source** to the `main` branch / `/(root)`.
4. GitHub will publish the site at `https://<username>.github.io/Blog-Website/`.

### Other Static Hosts

- **Netlify**: Drag-and-drop the repository directory or connect via Git.
- **Vercel**: Import the repository directly.
- **Firebase Hosting**: Initialize and deploy:
  ```bash
  firebase init hosting
  firebase deploy
  ```

## Troubleshooting

| Issue | Solution |
|---|---|
| Images do not load | Ensure an active internet connection; images are fetched dynamically from `picsum.photos`. |
| Avatars appear broken | Verify the DiceBear API URL structure or update the seed parameter. |
| CSS not applied via `file://` | Certain browser security settings block external resources on `file://`. Use a local HTTP server (`python -m http.server`). |
| Layout looks broken on mobile | Verify that the viewport meta tag (`<meta name="viewport" content="width=device-width, initial-scale=1">`) is present in `index.html`. |
| Want to add dark mode | Define `:root { --bg-color: #111; --text-color: #eee; --container-bg: #222; }` in `style.css` and toggle via a body class. |
| Container appears off-center | Ensure `style.css` is updated to load the latest Flexbox centering rules. |

## Roadmap

- **JavaScript integration**: Load dynamic blog post data from a JSON file or headless CMS.
- **Dark mode**: Add an interactive theme toggle using CSS custom properties.
- **Search & filter**: Implement category-based content filtering UI.
- **Accessibility audit**: Implement ARIA roles, keyboard navigation, and contrast improvements.
- **Full-stack conversion**: Add a backend API (Node/Express or Django) with a database for post persistence.

## Contributing

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature/awesome-feature
   ```
3. Commit your changes with clear messages.
4. Push to your branch:
   ```bash
   git push origin feature/awesome-feature
   ```
5. Open a Pull Request describing your changes.

### Pull Request Checklist

- [ ] Code follows project style guidelines.
- [ ] HTML is semantic and accessible.
- [ ] CSS is lint-free.
- [ ] README is updated for new features or usage instructions.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/imaakarsh/Blog-Website/blob/main/LICENSE) file for details.

## Acknowledgements

- [DiceBear](https://dicebear.com) – Avatar generation
- [Picsum Photos](https://picsum.photos) – Placeholder images
- [Shields.io](https://shields.io) – Badges

## Author

**Aakarsh** – Aspiring Web / Full-Stack Developer  
[GitHub Profile](https://github.com/imaakarsh)