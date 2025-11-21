# FreeSTAR Network Wiki

This repository contains multiple wikis for various FreeSTAR Network projects, all built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## 🎯 Available Wikis

- **[FreeSTAR Everywhere](wikis/everywhere/)** - VoIP service for licensed amateur radio operators
- **[FreeSTAR Multi-Mode](wikis/multi-mode/)** - Versatile multi-mode communication platform
- **[FreeSTAR SystemX](wikis/systemx/)** - Network management system for amateur radio
- **[FreeSTAR ModuleX](wikis/modulex/)** - Modular component system for custom solutions

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/FreeSTAR-Network/wiki.git
   cd wiki
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Building All Wikis

Build all wikis at once using the build script:

```bash
python build_all_wikis.py
```

This will build all wikis and create a unified site structure accessible via `index.html`.

### Building Individual Wikis

To build a specific wiki:

```bash
cd wikis/everywhere
mkdocs build
```

Replace `everywhere` with any wiki name: `multi-mode`, `systemx`, or `modulex`.

### Local Development

To serve a wiki locally with live reload:

```bash
cd wikis/everywhere
mkdocs serve
```

Then visit [http://localhost:8000](http://localhost:8000) in your browser.

## 📝 Contributing to Wikis

### Adding a New Page

1. Navigate to the wiki's `docs` folder:
   ```bash
   cd wikis/[wiki-name]/docs
   ```

2. Create a new Markdown file:
   ```bash
   touch new-page.md
   ```

3. Add content using Markdown syntax

4. Update the wiki's `mkdocs.yml` navigation:
   ```yaml
   nav:
     - Home: index.md
     - New Page: new-page.md  # Add this line
   ```

### Adding External Documentation

To link to external documentation:

1. Edit the wiki's `mkdocs.yml` file
2. Add an external link in the navigation:
   ```yaml
   nav:
     - Home: index.md
     - External Docs: https://example.com/docs
   ```

### Adding Images

1. Place images in the wiki's `docs/img/` folder:
   ```bash
   cp image.png wikis/[wiki-name]/docs/img/
   ```

2. Reference in Markdown:
   ```markdown
   ![Alt text](img/image.png)
   ```

## 🎨 Theme Customization

Each wiki features a modern, glossy design with light/dark mode support:

- **Light/Dark Mode Toggle**: Automatically detects system preference and allows manual switching
- **Unique Color Schemes**: Each wiki has distinct colors for easy identification
- **Modern Icons**: Material Design icons for visual appeal
- **Glossy Effects**: Enhanced shadows and hover effects for a polished look

### Customizing a Wiki's Appearance

Edit the wiki's `mkdocs.yml` file:

```yaml
theme:
  palette:
    - scheme: default
      primary: blue  # Change primary color
      accent: orange  # Change accent color
```

Available colors: `red`, `pink`, `purple`, `deep purple`, `indigo`, `blue`, `light blue`, `cyan`, `teal`, `green`, `light green`, `lime`, `yellow`, `amber`, `orange`, `deep orange`

### Custom CSS

Each wiki includes custom CSS in `docs/stylesheets/extra.css` for additional styling.

## 🆕 Adding a New Wiki

1. Create the wiki directory structure:
   ```bash
   mkdir -p wikis/new-wiki/docs/stylesheets
   ```

2. Copy a template configuration:
   ```bash
   cp wikis/everywhere/mkdocs.yml wikis/new-wiki/
   cp wikis/everywhere/docs/stylesheets/extra.css wikis/new-wiki/docs/stylesheets/
   ```

3. Update `mkdocs.yml` with the new wiki details:
   ```yaml
   site_name: FreeSTAR New Wiki
   site_url: https://freestar-network.github.io/wiki/new-wiki/
   ```

4. Create initial documentation pages:
   ```bash
   touch wikis/new-wiki/docs/index.md
   touch wikis/new-wiki/docs/about.md
   ```

5. Update `index.html` to include the new wiki card

6. Update `.github/workflows/deploy.yml` to build the new wiki

## 📚 Documentation Structure

```
wiki/
├── index.html                 # Main landing page
├── requirements.txt           # Python dependencies
├── build_all_wikis.py        # Build script
├── wikis/
│   ├── everywhere/
│   │   ├── mkdocs.yml        # Wiki configuration
│   │   └── docs/
│   │       ├── index.md      # Home page
│   │       ├── about.md
│   │       ├── img/          # Images
│   │       └── stylesheets/
│   │           └── extra.css # Custom styles
│   ├── multi-mode/
│   │   └── [same structure]
│   ├── systemx/
│   │   └── [same structure]
│   └── modulex/
│       └── [same structure]
└── .github/
    └── workflows/
        └── deploy.yml         # GitHub Actions deployment
```

## 🔧 Advanced Features

### Code Syntax Highlighting

All wikis support syntax highlighting for various languages:

````markdown
```python
def hello_world():
    print("Hello, FreeSTAR!")
```
````

### Admonitions (Callouts)

Use admonitions for important notes:

```markdown
!!! note "Important Note"
    This is an important note that stands out.

!!! warning "Warning"
    Be careful with this operation.

!!! tip "Pro Tip"
    Here's a helpful tip for users.
```

### Tabs

Create tabbed content:

```markdown
=== "Tab 1"
    Content for tab 1

=== "Tab 2"
    Content for tab 2
```

### Task Lists

```markdown
- [x] Completed task
- [ ] Pending task
- [ ] Another task
```

## 🚀 Deployment

The repository uses GitHub Actions to automatically build and deploy all wikis to GitHub Pages when changes are pushed to the `main` branch.

### Manual Deployment

```bash
python build_all_wikis.py
# Commit and push the generated site/ directory
```

## 📖 MkDocs Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Guide](https://www.markdownguide.org/)

## 🤝 Contributing

We welcome contributions! To contribute:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with `mkdocs serve`
5. Submit a pull request

## 📄 License

This documentation is maintained by the FreeSTAR Network for licensed amateur radio operators.

## 🔗 Links

- [FreeSTAR Network Website](https://freestar.network)
- [GitHub Organization](https://github.com/FreeSTAR-Network)

---

**Note**: All FreeSTAR services are designed exclusively for licensed amateur radio operators.