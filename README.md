# 📝 Aakarsh's Blogs  

![HTML5](https://img.shields.io/badge/HTML5-%23E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-%231572B6?logo=css3&logoColor=white) ![License](https://img.shields.io/badge/License-MIT-brightgreen) ![Stars](https://img.shields.io/github/stars/imaakarsh/Blog-Website?style=social) ![Issues](https://img.shields.io/github/issues/imaakarsh/Blog-Website)  

**A clean, responsive, and fully static blog‑website UI built with HTML5 & CSS3.**  
The project showcases modern layout techniques (CSS Grid & Flexbox), card‑based UI patterns, hover animations, and responsive design without any JavaScript.

---  

## 🚀 Project Overview  

**Aakarsh's Blogs** is a static front‑end prototype that displays a collection of blog posts in a modern, card‑driven grid. Each card contains:

- A featured image (sourced from **Picsum Photos**)  
- Blog title & short description  
- Author avatar (generated via **DiceBear API**)  
- Category tag  

The layout adapts gracefully from mobile to desktop, providing a solid foundation for a future full‑stack blog application.

---  

## ✨ Features  

| Feature | Description | Status |
|---------|-------------|--------|
| 📱 Fully responsive grid | CSS Grid + media queries adapt to any viewport | ✅ Stable |
| 🖼️ Image hover zoom | Subtle scale transform on hover for featured images | ✅ Stable |
| 🧩 Card‑based design | Consistent UI pattern for each blog entry | ✅ Stable |
| 👤 Author avatar | Dynamic avatar from DiceBear API | ✅ Stable |
| 🏷️ Category tags | Color‑coded tags for quick content filtering | ✅ Stable |
| ⚡ Clean code structure | Semantic HTML, BEM‑style CSS naming | ✅ Stable |
| 🎨 Refactored body & container styles | Updated background color and container layout for a cleaner, more centered appearance | ✅ Stable |
| 🌙 Dark‑mode placeholder | CSS variables prepared for future dark theme | ⚙️ Planned |

---  

## 🛠️ Tech Stack  

| Layer | Technology | Purpose |
|-------|------------|---------|
| Markup | **HTML5** | Semantic page structure |
| Styling | **CSS3** (Grid, Flexbox, Variables) | Layout, responsiveness, theming |
| Images | **Picsum Photos** | Random placeholder images |
| Avatars | **DiceBear API** | Dynamic author avatars |
| Hosting (optional) | **GitHub Pages** | Free static site deployment |

---  

## 🏗️ Architecture & Directory Layout  

```
Blog-Website/
├── index.html          # Main entry point – static HTML page
├── style.css           # Global stylesheet (Grid, Flexbox, utilities)
├── image.png           # Project logo / banner (used in README)
└── README.md           # Documentation (this file)
```

*All assets are loaded from external services; no local images or scripts are required.*  

The project follows a **single‑page static architecture**: the browser loads `index.html` and `style.css`, then renders the UI entirely on the client side.

---  

## 📦 Getting Started  

### Prerequisites  

- A modern web browser (Chrome, Firefox, Edge, Safari)  
- Optional: a local HTTP server for testing (Node, Python, or any static‑file server)

### Installation  

1. **Clone the repository**  

   ```bash
   git clone https://github.com/imaakarsh/Blog-Website.git
   cd Blog-Website
   ```

2. **Open the site**  

   - **Option A – Direct file open**  
     Double‑click `index.html` or open it via `file://` in your browser.  
   - **Option B – Local HTTP server (recommended for Chrome security)**  

     ```bash
     # Using Python (built‑in)
     python -m http.server 8000
     
     # Using Node (serve package)
     npx serve .
     
     # Using Docker
     docker run -v "$PWD":/usr/share/nginx/html:ro -p 8080:80 nginx
     ```

   Then navigate to `http://localhost:8000` (or the appropriate port).

### Verification  

You should see a grid of blog cards similar to the screenshot below. Resize the browser window to confirm the responsive behavior and notice the updated background and centered container layout.

---  

## 🎬 Usage  

The site is static; no runtime configuration is required. Below are common usage scenarios:

| Scenario | Steps |
|----------|-------|
| **View the homepage** | Open `index.html` in a browser. |
| **Test responsiveness** | Resize the viewport or open DevTools → Device Toolbar. |
| **Replace placeholder images** | Edit the `src` attribute of `<img>` tags in `index.html` to point to your own images. |
| **Change author avatars** | Update the `src` URL of the avatar image (DiceBear API) with a different seed or style. |
| **Add a new blog card** | Copy an existing `<article class="card">` block, modify its content, and paste it inside the `<section class="grid">`. |

### Example: Adding a New Card  

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

---  

## 🛠️ Development  

### Setting Up a Development Environment  

1. **Editor** – Any code editor (VS Code, Sublime, etc.) with HTML/CSS linting.  
2. **Live‑reload (optional)** – Install the VS Code extension *Live Server* or run `npx serve` for instant refresh on file changes.  

### Code Style Guidelines  

- **HTML** – Use semantic tags (`<section>`, `<article>`, `<header>`, `<footer>`).  
- **CSS** – Follow BEM naming (`block__element--modifier`). Keep selectors specific but avoid deep nesting.  
- **Indentation** – 2 spaces (no tabs).  
- **Comments** – Use `/* comment */` in CSS; HTML comments `<!-- comment -->` sparingly.  

#### Recent CSS Refactor  

- **Body background** now uses the CSS variable `--bg-color` for easy theming.  
- **Text color** is managed via the new variable `--text-color`, allowing quick theme switches.  
- **Container layout** switched to a Flexbox‑based centering approach, improving vertical alignment on tall viewports.  
- Added a **container background variable** (`--container-bg`) to make future theming (e.g., dark mode) straightforward.  

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

### Running Tests  

The project does not contain automated tests. For visual regression, open the page in multiple browsers and verify layout consistency.

---  

## 🚀 Deployment  

Because the site is static, deployment is straightforward.

### GitHub Pages (recommended)  

1. Push the repository to GitHub.  
2. In the repository settings, enable **Pages** → Source: `main` branch / `/(root)`.  
3. GitHub will publish the site at `https://<username>.github.io/Blog-Website/`.  

### Other Static Hosts  

- **Netlify** – Drag‑and‑drop the repository folder or connect via Git.  
- **Vercel** – Same as Netlify, just import the repo.  
- **Firebase Hosting** – `firebase init hosting` then `firebase deploy`.  

All hosts serve the files exactly as they appear locally; no build step is required.

---  

## 📚 FAQ & Troubleshooting  

| Issue | Solution |
|-------|----------|
| **Images do not load** | Ensure you have an active internet connection; images are fetched from `picsum.photos`. |
| **Avatars appear broken** | Verify the DiceBear API URL is correct; you can replace the seed value to generate a new avatar. |
| **CSS not applied when opening via `file://`** | Some browsers block external resources on `file://`. Use a local HTTP server (`python -m http.server`). |
| **Layout looks broken on mobile** | Confirm that the viewport meta tag is present in `index.html` (`<meta name="viewport" content="width=device-width, initial-scale=1">`). |
| **Want to add dark mode** | Edit `style.css` to define `:root { --bg-color: #111; --text-color: #eee; --container-bg: #222; }` and toggle via a class on `<body>`. |
| **Container appears off‑center** | The recent CSS refactor uses Flexbox centering; ensure you are loading the latest `style.css`. |

---  

## 🗺️ Roadmap  

- **JavaScript integration** – Dynamic blog loading from a JSON file or headless CMS.  
- **Dark mode** – Theme toggle with CSS custom properties.  
- **Search & filter** – Category‑based filtering UI.  
- **Accessibility audit** – ARIA roles, keyboard navigation, color contrast.  
- **Full‑stack conversion** – Backend API (Node/Express or Django) with a database for persistent posts.  

---  

## 🤝 Contributing  

Contributions are welcome! Please follow these steps:

1. **Fork** the repository.  
2. **Create a feature branch** (`git checkout -b feature/awesome‑feature`).  
3. **Commit** your changes with clear messages.  
4. **Push** to your fork (`git push origin feature/awesome‑feature`).  
5. Open a **Pull Request** describing the changes.  

### Pull Request Checklist  

- [ ] Code follows the style guidelines above.  
- [ ] New/modified HTML is semantic and accessible.  
- [ ] CSS is lint‑free (`stylelint` optional).  
- [ ] Updated the README if you added new features or usage instructions.  

---  

## 📄 License  

This project is licensed under the **MIT License** – see the [LICENSE](https://github.com/imaakarsh/Blog-Website/blob/main/LICENSE) file for details.

---  

## 🙏 Credits & Acknowledgments  

- **DiceBear** – Avatar generation (`https://dicebear.com`).  
- **Picsum Photos** – Placeholder images (`https://picsum.photos`).  
- **Shields.io** – Badges used in this README.  

---  

## 👨‍💻 Author  

**Aakarsh** – Aspiring Web / Full‑Stack Developer  
[GitHub Profile](https://github.com/imaakarsh)  

Happy coding! 🚀