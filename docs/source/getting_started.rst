# Getting Started

Welcome to GrowKitty! This guide will help you set up the project for development or local use.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- **Git**: For version control and cloning the repository
- **Web Browser**: Modern browser (Chrome, Firefox, Safari, or Edge)
- **Text Editor or IDE**: VS Code, Sublime Text, or your preferred editor
- **Node.js** (optional): For running a local development server

## Quick Start

### 1. Clone the Repository

Open your terminal and run:

```bash
git clone https://github.com/GrowKitty/GrowKitty.git
cd GrowKitty
```

### 2. Open the Project

Since GrowKitty is a vanilla JavaScript web application, you can start immediately without installing dependencies.

#### Option A: Open Directly in Browser

Navigate to the project directory and open `index.html` in your browser:

```bash
# On macOS
open index.html

# On Linux
xdg-open index.html

# On Windows
start index.html
```

#### Option B: Use a Local Development Server (Recommended)

Using a local server prevents CORS issues and provides a better development experience.

**Using Python (comes pre-installed on most systems):**

```bash
# Python 3
python3 -m http.server 8000

# Then open http://localhost:8000 in your browser
```

**Using Node.js http-server:**

```bash
# Install http-server globally (one-time setup)
npm install -g http-server

# Run server
http-server -p 8000

# Then open http://localhost:8000 in your browser
```

**Using VS Code Live Server Extension:**

1. Install the "Live Server" extension in VS Code
2. Right-click on `index.html`
3. Select "Open with Live Server"

### 3. Explore the Application

Once running, you should see the GrowKitty home page. You can now:

- Create your first habit
- Receive daily missions
- Start caring for your virtual cat
- Track your progress on the dashboard

## Project Structure

Understanding the project structure will help you navigate and contribute:

```
GrowKitty/
├── index.md                 # Main landing page
├── features.md              # Features page
├── community.md             # Community page
├── contact.md               # Contact page
├── src/                     # Source code
│   ├── js/                  # JavaScript files
│   ├── css/                 # Stylesheets
│   └── assets/              # Images and other assets
├── docs/                    # Documentation files
├── tests/                   # Test files
├── assets/                  # Static assets
├── _layouts/                # Jekyll layouts for GitHub Pages
├── script.js                # Main application script
├── README.md                # Project overview
├── CONTRIBUTING.md          # Contribution guidelines
├── CODE_OF_CONDUCT.md       # Community guidelines
└── LICENSE                  # MIT License
```

## Development Workflow

### Making Changes

1. **Create a new branch** for your feature or fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** in the appropriate files:
   - UI changes: Edit HTML/CSS files
   - Logic changes: Edit JavaScript files
   - Documentation: Edit markdown files in `docs/`

3. **Test your changes** by opening the application in your browser and verifying functionality

4. **Commit your changes** with a descriptive message:
   ```bash
   git add .
   git commit -m "Add: brief description of your changes"
   ```

### Code Style Guidelines

- Use **2 spaces** for indentation in JavaScript and CSS
- Follow **camelCase** naming convention for JavaScript variables and functions
- Use **kebab-case** for CSS classes
- Add **comments** for complex logic
- Keep functions **small and focused** on a single task
- Write **descriptive variable names** instead of abbreviations

### Testing Your Changes

Before submitting changes:

1. **Test all features** affected by your changes
2. **Check responsiveness** on different screen sizes
3. **Test in multiple browsers** (Chrome, Firefox, Safari)
4. **Verify no console errors** appear in browser DevTools
5. **Check accessibility** using browser accessibility tools

## Running Tests

If you're working on test files:

```bash
cd tests
# Open test files in browser or run with your preferred test runner
```

## Building Documentation

GrowKitty uses Read the Docs for documentation. To preview documentation locally:

1. Install Sphinx (Python documentation generator):
   ```bash
   pip install sphinx sphinx-rtd-theme
   ```

2. Build the documentation:
   ```bash
   cd docs
   make html
   ```

3. Open the generated documentation:
   ```bash
   # The built files are in docs/_build/html/
   open _build/html/index.html
   ```

## Troubleshooting

### Common Issues

**Problem: Files not loading or "Cannot find module" errors**
- **Solution**: Make sure you're using a local development server, not opening `index.html` directly

**Problem: Changes not appearing in browser**
- **Solution**: Hard refresh your browser (Ctrl+Shift+R or Cmd+Shift+R) to clear cache

**Problem: Cat animations not working**
- **Solution**: Check browser console for JavaScript errors and ensure all asset files are present

**Problem: Can't push to repository**
- **Solution**: Ensure you have proper permissions and are working on a fork of the repository

### Getting Help

If you encounter issues:

1. Check the [GitHub Issues](https://github.com/GrowKitty/GrowKitty/issues) for existing solutions
2. Review the [Contributing Guidelines](https://github.com/GrowKitty/GrowKitty/blob/main/CONTRIBUTING.md)
3. Join community discussions in the repository
4. Contact the team through the [Contact page](contact.md)

## Next Steps

Now that you have GrowKitty running locally, you can:

1. **Explore the codebase** to understand how features are implemented
2. **Read the [Contributing Guidelines](https://github.com/GrowKitty/GrowKitty/blob/main/CONTRIBUTING.md)** to learn how to submit changes
3. **Check open issues** on GitHub for ways to contribute
4. **Join the community** to connect with other contributors
5. **Build your first habit** and experience the app as a user

## Contributing

We welcome contributions from everyone! Here's how to get started:

1. **Fork the repository** on GitHub
2. **Create a feature branch** from `main`
3. **Make your changes** following our code style guidelines
4. **Test thoroughly** to ensure nothing breaks
5. **Submit a pull request** with a clear description of your changes

For detailed contribution guidelines, see [CONTRIBUTING.md](https://github.com/GrowKitty/GrowKitty/blob/main/CONTRIBUTING.md).

## Community Resources

- **Repository**: [github.com/GrowKitty/GrowKitty](https://github.com/GrowKitty/GrowKitty)
- **Documentation**: [growkitty.readthedocs.io](https://growkitty.readthedocs.io)
- **Issues**: [GitHub Issues](https://github.com/GrowKitty/GrowKitty/issues)
- **Discussions**: [GitHub Discussions](https://github.com/GrowKitty/GrowKitty/discussions)

## License

GrowKitty is released under the [MIT License](https://github.com/GrowKitty/GrowKitty/blob/main/LICENSE). You're free to use, modify, and distribute this software for any purpose, commercial or non-commercial.

---

Ready to start growing your kitty? Let's build better habits together! 🐱✨
