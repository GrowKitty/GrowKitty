# Contributing to GrowKitty

Thank you for your interest in contributing to GrowKitty! 🐱✨

We welcome contributions from everyone. This document provides guidelines for contributing to the project.

## Table of Contents
- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Issue Reporting](#issue-reporting)

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment for all contributors. Please:
- Be respectful and constructive in discussions
- Welcome newcomers and help them get started
- Focus on what is best for the community
- Show empathy towards other community members

## How Can I Contribute?

### 🐛 Reporting Bugs
- Check if the bug has already been reported in [Issues](https://github.com/lillian-na/GrowKitty/issues)
- Use the bug report template when creating a new issue
- Include steps to reproduce, expected behavior, and actual behavior
- Add screenshots if applicable

### 💡 Suggesting Features
- Check existing [Issues](https://github.com/lillian-na/GrowKitty/issues) and [Discussions](https://github.com/lillian-na/GrowKitty/discussions)
- Describe the feature and its benefits clearly
- Explain use cases and how it aligns with GrowKitty's goals

### 🎨 Design Contributions
- Follow the existing UI/UX design patterns
- Ensure designs are accessible and user-friendly
- Share mockups or prototypes in the issue discussion

### 💻 Code Contributions
- Pick an issue labeled `good first issue` or `help wanted`
- Comment on the issue to let others know you're working on it
- Follow the coding standards and commit guidelines
- Submit a pull request when ready

## Development Setup

### Prerequisites
- Git
- Modern web browser (Chrome, Firefox, Safari, or Edge)
- Code editor (VS Code recommended)
- Basic knowledge of HTML, CSS, and JavaScript

### Getting Started
1. **Fork the repository**
   ```bash
   # Click the 'Fork' button on GitHub
   ```

2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR-USERNAME/GrowKitty.git
   cd GrowKitty
   ```

3. **Create a new branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

4. **Open the project**
   - Open `index.html` in your browser
   - Or use a local server (e.g., Live Server in VS Code)

5. **Make your changes**
   - Write clean, well-documented code
   - Test your changes thoroughly

## Coding Standards

### JavaScript
- Use ES6+ features where appropriate
- Use `const` and `let` instead of `var`
- Use meaningful variable and function names
- Add comments for complex logic
- Keep functions small and focused

```javascript
// Good
const calculateHabitSuccessRate = (completedDays, totalDays) => {
  if (totalDays === 0) return 0;
  return Math.round((completedDays / totalDays) * 100);
};

// Avoid
var x = function(a, b) {
  return Math.round((a / b) * 100);
};
```

### HTML
- Use semantic HTML5 elements
- Include appropriate ARIA labels for accessibility
- Keep markup clean and well-indented

### CSS
- Use consistent naming conventions
- Organize styles logically (layout, components, utilities)
- Comment major sections
- Ensure responsive design

### File Organization
```
GrowKitty/
├── src/
│   ├── cat.js
│   ├── dashboard.js
│   ├── mission.js
│   └── reward.js
├── LICENSE
├── README.md
├── index.html
├── script.js
└── style.css
```

## Commit Guidelines

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification.

### Commit Message Format
```
<type>(<scope>): <subject>

[optional body]

[optional footer(s)]
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

### Examples
```bash
feat(missions): add random daily mission generator

fix(cat): resolve cat animation not playing on iOS

docs(readme): update installation instructions

style(css): improve responsive layout for mobile devices
```

## Pull Request Process

1. **Update your branch**
   ```bash
   git fetch origin
   git rebase origin/main
   ```

2. **Test your changes**
   - Test on multiple browsers
   - Check responsive design
   - Verify no console errors

3. **Push your branch**
   ```bash
   git push origin feature/your-feature-name
   ```

4. **Create a Pull Request**
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your branch
   - Fill out the PR template with:
     - Clear description of changes
     - Related issue numbers (e.g., "Closes #123")
     - Screenshots if UI changes
     - Testing steps

5. **Code Review**
   - Address reviewer feedback
   - Make necessary changes
   - Push updates to the same branch

6. **Merge**
   - Once approved, a maintainer will merge your PR
   - Delete your branch after merging

## Issue Reporting

### Bug Report Template
```markdown
**Describe the bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce:
1. Go to '...'
2. Click on '...'
3. See error

**Expected behavior**
What you expected to happen.

**Screenshots**
If applicable, add screenshots.

**Environment:**
- OS: [e.g., Windows 10, macOS 13]
- Browser: [e.g., Chrome 120, Firefox 121]
- Version: [e.g., 1.0.0]

**Additional context**
Any other context about the problem.
```

### Feature Request Template
```markdown
**Is your feature request related to a problem?**
A clear description of what the problem is.

**Describe the solution you'd like**
What you want to happen.

**Describe alternatives you've considered**
Other solutions you've thought about.

**Additional context**
Mockups, examples, or any other context.
```

## Communication

- **GitHub Issues**: For bug reports and feature requests
- **GitHub Discussions**: For questions and general discussion
- **Pull Requests**: For code review and collaboration
- **KakaoTalk/Zoom**: For team communication (internal)

## Recognition

All contributors will be recognized in our [Contributors](https://github.com/lillian-na/GrowKitty/graphs/contributors) page.

## Questions?

Feel free to reach out by:
- Opening an [Issue](https://github.com/lillian-na/GrowKitty/issues) for bug reports and feature requests
- Commenting on relevant issues
- Contacting the project maintainers

Thank you for contributing to GrowKitty! 🐱💚
