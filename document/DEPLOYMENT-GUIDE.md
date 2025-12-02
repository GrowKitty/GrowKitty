# GrowKitty Documentation Deployment Guide

This guide walks you through deploying your Sphinx documentation to ReadTheDocs.

## 📁 Documentation Structure

Your `docs/` folder should have this structure:

```
docs/
├── conf.py                    # Sphinx configuration
├── index.rst                  # Documentation homepage
├── introduction.rst           # Project introduction
├── getting-started.rst        # Installation guide
├── usage.rst                  # Usage instructions
├── technical-overview.rst     # Architecture & design
├── api-reference.rst          # API documentation
├── configuration.rst          # Configuration guide
├── troubleshooting.rst        # Troubleshooting help
├── contributing.rst           # Contribution guidelines
├── faq.rst                    # Frequently asked questions
├── release-notes.rst          # Version history
├── requirements.txt           # Python dependencies
├── Makefile                   # Build commands (Unix)
├── make.bat                   # Build commands (Windows)
├── _static/                   # Static assets (images, CSS)
│   ├── logo.png
│   ├── favicon.ico
│   └── growkitty-banner.png
└── _build/                    # Generated files (gitignored)
```

## 🚀 Step-by-Step Deployment

### 1. Prepare Your GitHub Repository

#### A. Commit Documentation to GitHub

```bash
# Navigate to your project root
cd GrowKitty

# Create docs directory if not exists
mkdir -p docs

# Copy all documentation files to docs/
# (Files provided in artifacts)

# Add to git
git add docs/
git add .readthedocs.yaml
git add README.md  # if updated

# Commit
git commit -m "docs: add Sphinx documentation with ReadTheDocs setup"

# Push to main branch
git push origin main
```

#### B. Verify File Structure

Ensure these files exist in your repository:

- ✅ `.readthedocs.yaml` (in root directory)
- ✅ `docs/conf.py`
- ✅ `docs/requirements.txt`
- ✅ `docs/index.rst`
- ✅ All other .rst files

### 2. Set Up ReadTheDocs Account

#### A. Sign Up/Login

1. Visit [readthedocs.org](https://readthedocs.org)
2. Click "Sign Up" or "Log In"
3. **Connect with GitHub** (recommended)

#### B. Import Your Project

1. Click "Import a Project"
2. Click "Import Manually" or select from GitHub list
3. Fill in project details:
   - **Name**: `GrowKitty`
   - **Repository URL**: `https://github.com/lillian-na/GrowKitty`
   - **Repository type**: Git
   - **Default branch**: `main`
   - **Default version**: `latest`
4. Click "Next"

### 3. Configure ReadTheDocs Settings

#### A. Admin Settings

Go to your project's admin panel:

1. **Settings** → **Advanced Settings**:
   - ✅ Enable "Build pull requests"
   - ✅ Enable "Build on commit"
   - ✅ Set Python interpreter: `CPython 3.12`
   - ✅ Documentation type: `Sphinx Html`
   - Configuration file: `.readthedocs.yaml`

2. **Settings** → **Environment Variables** (if needed):
   - Add any required environment variables

3. **Versions** → **Active Versions**:
   - ✅ Activate "latest"
   - ✅ Activate any tagged versions (e.g., `v1.0.0`)

#### B. Webhook Configuration (Automatic)

ReadTheDocs automatically sets up webhooks when you connect via GitHub. Verify:

1. Go to GitHub repository → Settings → Webhooks
2. You should see a ReadTheDocs webhook
3. It should have a green checkmark (successful pings)

### 4. Build Documentation

#### A. Trigger First Build

1. In ReadTheDocs dashboard, go to your project
2. Click "Build Version"
3. Select "latest"
4. Click "Build"

#### B. Monitor Build

- Watch the build log for errors
- Common issues:
  - Missing dependencies (check `requirements.txt`)
  - Syntax errors in RST files
  - Missing image files

#### C. Fix Build Errors (if any)

```bash
# Test build locally first
cd docs
make html

# Check for errors
# Fix issues in .rst files

# Commit and push fixes
git add docs/
git commit -m "docs: fix build errors"
git push origin main

# ReadTheDocs will auto-rebuild
```

### 5. Verify Deployment

#### A. Check Live Documentation

Your docs should be available at:
```
https://growkitty.readthedocs.io/
```

Or:
```
https://growkitty.readthedocs.io/en/latest/
```

#### B. Test All Pages

Navigate through and verify:
- ✅ Homepage loads correctly
- ✅ All sections accessible
- ✅ Navigation menu works
- ✅ Search functionality works
- ✅ Images display properly
- ✅ Code blocks render correctly
- ✅ Cross-references work

### 6. Add Documentation Badge

#### A. Get Badge Code

1. ReadTheDocs project → Admin → Badges
2. Copy badge markdown or RST

#### B. Add to README

```markdown
# In README.md
[![Documentation Status](https://readthedocs.org/projects/growkitty/badge/?version=latest)](https://growkitty.readthedocs.io/en/latest/?badge=latest)
```

### 7. Update README

Add documentation section (use `README-Documentation-Section.md` content):

```markdown
## 📚 Documentation

Comprehensive documentation is available on ReadTheDocs:

🔗 **[Read the Full Documentation](https://growkitty.readthedocs.io)**

### Quick Links
- [Getting Started](https://growkitty.readthedocs.io/en/latest/getting-started.html)
- [Usage Guide](https://growkitty.readthedocs.io/en/latest/usage.html)
- [API Reference](https://growkitty.readthedocs.io/en/latest/api-reference.html)
```

## 🧪 Testing Documentation Locally

### Prerequisites

```bash
# Install Python dependencies
pip install -r docs/requirements.txt
```

### Build and View

```bash
# Navigate to docs directory
cd docs

# Build HTML
make html

# Build PDF (optional)
make latexpdf

# Clean build files
make clean
```

### View in Browser

```bash
# macOS
open _build/html/index.html

# Linux
xdg-open _build/html/index.html

# Windows
start _build/html/index.html

# Or use Python server
cd _build/html
python -m http.server 8000
# Visit http://localhost:8000
```

### Watch for Changes (Development)

```bash
# Install sphinx-autobuild
pip install sphinx-autobuild

# Auto-rebuild on file changes
sphinx-autobuild docs docs/_build/html
# Visit http://127.0.0.1:8000
```

## 🔄 Continuous Updates

### Automatic Builds

ReadTheDocs automatically rebuilds when you:
- Push to `main` branch
- Create a new tag/release
- Submit a pull request (if enabled)

### Manual Rebuild

1. ReadTheDocs dashboard
2. Your project
3. Click "Build Version"
4. Select version and build

### Version Management

#### Creating a New Version

```bash
# Tag a release
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0

# ReadTheDocs will automatically:
# 1. Detect the new tag
# 2. Create a new version
# 3. Build documentation for it
```

#### Activating Versions

1. ReadTheDocs → Versions
2. Click "Edit" on version
3. Toggle "Active" → Save
4. Set as "Default" if desired

## 🎨 Customization

### Custom Domain (Optional)

1. ReadTheDocs → Admin → Domains
2. Add your custom domain (e.g., `docs.growkitty.app`)
3. Add DNS CNAME record:
   ```
   docs.growkitty.app CNAME growkitty.readthedocs.io
   ```

### Theme Customization

Edit `docs/conf.py`:

```python
html_theme_options = {
    'logo_only': True,
    'display_version': True,
    'prev_next_buttons_location': 'both',
    'style_external_links': True,
    # Add custom options...
}

# Custom CSS
html_static_path = ['_static']
html_css_files = ['custom.css']
```

### Adding Custom Styling

Create `docs/_static/custom.css`:

```css
/* Custom documentation styles */
.wy-side-nav-search {
    background-color: #8B5CF6;
}

.wy-menu-vertical a {
    color: #1F2937;
}
```

## 📊 Analytics (Optional)

### Google Analytics

In `docs/conf.py`:

```python
html_theme_options = {
    'analytics_id': 'G-XXXXXXXXXX',  # Your GA ID
    'analytics_anonymize_ip': True,
}
```

### ReadTheDocs Analytics

ReadTheDocs provides built-in analytics:
- Admin → Traffic Analytics
- View page views, popular pages, etc.

## 🐛 Troubleshooting

### Build Failures

**Check build log:**
1. ReadTheDocs → Builds → Click on failed build
2. Read error messages
3. Common issues:
   - Missing dependencies
   - RST syntax errors
   - Missing files

**Test locally:**
```bash
cd docs
make clean
make html
# Fix any errors shown
```

### Missing Images

- Ensure images are in `docs/_static/`
- Use relative paths in RST:
  ```rst
  .. image:: _static/logo.png
  ```

### Navigation Issues

- Check `toctree` directives in `index.rst`
- Ensure all referenced files exist
- Verify `maxdepth` settings

### Search Not Working

- Search is built automatically
- May take time after first deployment
- Rebuild if issues persist

## 📝 Documentation Maintenance

### Regular Updates

```bash
# Update docs
cd docs
edit <file>.rst

# Test locally
make clean && make html

# Commit and push
git add docs/
git commit -m "docs: update <description>"
git push origin main
```

### Adding New Pages

1. Create new `.rst` file in `docs/`
2. Add to `toctree` in `index.rst` or relevant section
3. Write content using RST syntax
4. Build and test locally
5. Commit and push

### Versioning Documentation

```bash
# For each release:
git tag -a v1.1.0 -m "Release 1.1.0"
git push origin v1.1.0

# Activate in ReadTheDocs
# Set default version if needed
```

## ✅ Deployment Checklist

Before going live, verify:

- [ ] All .rst files have no syntax errors
- [ ] All images exist and display correctly
- [ ] All code examples are tested and correct
- [ ] Cross-references work properly
- [ ] TOC navigation is logical
- [ ] README has documentation link
- [ ] ReadTheDocs badge is added
- [ ] Build succeeds without warnings
- [ ] All pages are accessible
- [ ] Search functionality works
- [ ] Mobile view is readable
- [ ] Links to external resources work

## 🎉 Success!

Your GrowKitty documentation is now live at:

**https://growkitty.readthedocs.io**

Share it with your users and contributors!

## 📞 Support

For issues with:
- **Documentation content**: Open issue on GitHub
- **ReadTheDocs platform**: Check [ReadTheDocs docs](https://docs.readthedocs.io)
- **Sphinx syntax**: See [Sphinx documentation](https://www.sphinx-doc.org)

---

**Next Steps:**
1. Share documentation link with community
2. Add to project website
3. Reference in issues/PRs
4. Keep documentation updated with code changes