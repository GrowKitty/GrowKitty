Contributing Guidelines
=======================

Thank you for your interest in contributing to GrowKitty! This document provides guidelines for contributing to the project.

Ways to Contribute
------------------

There are many ways to contribute to GrowKitty:

**Code Contributions**

- Bug fixes
- New features
- Performance improvements
- Code refactoring
- Test coverage

**Documentation**

- Improve existing docs
- Add tutorials
- Translate to other languages
- Fix typos and grammar
- Create video guides

**Design**

- UI/UX improvements
- Cat character designs
- Icon creation
- Animation work
- Accessibility enhancements

**Community**

- Answer questions
- Help troubleshoot issues
- Share feedback
- Test beta features
- Spread the word

Getting Started
---------------

Setting Up Development Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**1. Fork the Repository**

Visit `github.com/lillian-na/GrowKitty <https://github.com/lillian-na/GrowKitty>`_ and click "Fork"

**2. Clone Your Fork**

.. code-block:: bash

   git clone https://github.com/YOUR_USERNAME/GrowKitty.git
   cd GrowKitty

**3. Add Upstream Remote**

.. code-block:: bash

   git remote add upstream https://github.com/lillian-na/GrowKitty.git

**4. Create a Branch**

.. code-block:: bash

   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/bug-description

**5. Install Development Dependencies** (Optional)

.. code-block:: bash

   npm install
   # or
   yarn install

Development Workflow
~~~~~~~~~~~~~~~~~~~~

**1. Keep Your Fork Updated**

.. code-block:: bash

   git fetch upstream
   git checkout main
   git merge upstream/main
   git push origin main

**2. Make Your Changes**

- Write clean, readable code
- Follow existing code style
- Add comments where necessary
- Test your changes thoroughly

**3. Test Locally**

.. code-block:: bash

   # Start local server
   python -m http.server 8000
   
   # Or with Node.js
   npx http-server -p 8000
   
   # Visit http://localhost:8000

**4. Commit Your Changes**

.. code-block:: bash

   git add .
   git commit -m "feat: add new mission type"
   
   # Or for bug fixes
   git commit -m "fix: resolve streak calculation issue"

**5. Push to Your Fork**

.. code-block:: bash

   git push origin feature/your-feature-name

**6. Create Pull Request**

- Go to your fork on GitHub
- Click "New Pull Request"
- Fill out PR template
- Wait for review

Code Guidelines
---------------

JavaScript Style
~~~~~~~~~~~~~~~~

**General Principles**

- Use ES6+ features
- Prefer const over let, avoid var
- Use arrow functions appropriately
- Keep functions small and focused
- Write self-documenting code

**Naming Conventions**

.. code-block:: javascript

   // Variables and functions: camelCase
   const habitList = [];
   function calculateStreak() { }
   
   // Classes: PascalCase
   class HabitManager { }
   
   // Constants: UPPER_SNAKE_CASE
   const MAX_HABITS = 50;
   const DEFAULT_THEME = 'light';
   
   // Private methods: _prefixWithUnderscore
   function _internalHelper() { }

**Code Structure**

.. code-block:: javascript

   // Good: Clear and concise
   const getActiveHabits = () => {
     return habits.filter(h => h.active);
   };
   
   // Bad: Unclear and verbose
   const get_active = function() {
     var result = [];
     for (var i = 0; i < habits.length; i++) {
       if (habits[i].active == true) {
         result.push(habits[i]);
       }
     }
     return result;
   };

**Comments**

.. code-block:: javascript

   /**
    * Calculates the current streak for a habit
    * @param {string} habitId - The habit identifier
    * @param {Date} endDate - Optional end date (defaults to today)
    * @returns {number} Number of consecutive days
    */
   function calculateStreak(habitId, endDate = new Date()) {
     // Get completions sorted by date
     const completions = getCompletions(habitId)
       .sort((a, b) => b.date - a.date);
     
     let streak = 0;
     let checkDate = endDate;
     
     // Count consecutive days
     for (const completion of completions) {
       if (isSameDay(completion.date, checkDate)) {
         streak++;
         checkDate = subtractDays(checkDate, 1);
       } else {
         break; // Streak broken
       }
     }
     
     return streak;
   }

HTML/CSS Style
~~~~~~~~~~~~~~

**HTML**

- Use semantic HTML5 tags
- Include alt text for images
- Maintain proper indentation
- Close all tags properly

.. code-block:: html

   <!-- Good -->
   <section class="habits-container">
     <h2>Your Habits</h2>
     <ul class="habit-list">
       <li class="habit-item">
         <input type="checkbox" id="habit-1" />
         <label for="habit-1">Morning Exercise</label>
       </li>
     </ul>
   </section>
   
   <!-- Bad -->
   <div class="habits">
     <div class="title">Your Habits</div>
     <div class="list">
       <div><input type="checkbox"><span>Morning Exercise</span></div>
     </div>
   </div>

**CSS**

- Use class selectors over IDs
- Follow BEM naming convention
- Mobile-first approach
- Keep specificity low

.. code-block:: css

   /* Good: BEM naming */
   .habit-card {
     padding: 1rem;
     border-radius: 0.5rem;
   }
   
   .habit-card__title {
     font-size: 1.125rem;
     font-weight: 600;
   }
   
   .habit-card__title--completed {
     text-decoration: line-through;
     color: var(--gray-400);
   }
   
   /* Bad: Generic naming */
   .card {
     padding: 16px;
   }
   
   .card h3 {
     font-size: 18px;
   }
   
   .done {
     text-decoration: line-through;
   }

Git Commit Guidelines
~~~~~~~~~~~~~~~~~~~~~

**Commit Message Format**

.. code-block:: text

   <type>(<scope>): <subject>
   
   <body>
   
   <footer>

**Types**

- ``feat``: New feature
- ``fix``: Bug fix
- ``docs``: Documentation changes
- ``style``: Code style (formatting, semicolons)
- ``refactor``: Code refactoring
- ``test``: Adding tests
- ``chore``: Maintenance tasks

**Examples**

.. code-block:: bash

   # Feature
   git commit -m "feat(missions): add weekly challenge system"
   
   # Bug fix
   git commit -m "fix(habits): correct streak calculation for timezones"
   
   # Documentation
   git commit -m "docs(readme): update installation instructions"
   
   # Multiple changes
   git commit -m "feat(cat): add new accessories and animations
   
   - Add 5 new hat options
   - Implement purring animation
   - Fix accessory z-index issues
   
   Closes #42"

Pull Request Process
--------------------

Before Submitting
~~~~~~~~~~~~~~~~~

**Checklist:**

- [ ] Code follows project style guidelines
- [ ] All tests pass (if applicable)
- [ ] Documentation updated (if needed)
- [ ] Commit messages follow conventions
- [ ] Branch is up to date with main
- [ ] No merge conflicts
- [ ] Changes are focused and atomic

PR Template
~~~~~~~~~~~

Use this template for pull requests:

.. code-block:: markdown

   ## Description
   Brief description of changes made.
   
   ## Type of Change
   - [ ] Bug fix (non-breaking change fixing an issue)
   - [ ] New feature (non-breaking change adding functionality)
   - [ ] Breaking change (fix or feature causing existing functionality to change)
   - [ ] Documentation update
   
   ## How Has This Been Tested?
   Describe the tests you ran and how to reproduce.
   
   ## Screenshots (if applicable)
   Add screenshots showing the changes.
   
   ## Checklist
   - [ ] My code follows the project's style guidelines
   - [ ] I have performed a self-review of my own code
   - [ ] I have commented my code where necessary
   - [ ] I have updated the documentation accordingly
   - [ ] My changes generate no new warnings
   - [ ] I have tested this thoroughly
   
   ## Related Issues
   Closes #(issue number)

Review Process
~~~~~~~~~~~~~~

**What Happens Next:**

1. **Automated Checks** (if configured)
   
   - Linting
   - Tests
   - Build verification

2. **Code Review**
   
   - Maintainers review your code
   - May request changes
   - Discussion and feedback

3. **Iteration**
   
   - Address feedback
   - Push updates to same branch
   - Review continues

4. **Merge**
   
   - Once approved, PR is merged
   - Branch can be deleted
   - Changes go live

**Tips for Faster Review:**

- Keep PRs small and focused
- Write clear descriptions
- Respond to feedback promptly
- Be patient and respectful

Reporting Issues
----------------

Bug Reports
~~~~~~~~~~~

Use this template:

.. code-block:: markdown

   ## Bug Description
   Clear description of the bug.
   
   ## Steps to Reproduce
   1. Go to '...'
   2. Click on '...'
   3. Scroll down to '...'
   4. See error
   
   ## Expected Behavior
   What should happen.
   
   ## Actual Behavior
   What actually happens.
   
   ## Screenshots
   If applicable, add screenshots.
   
   ## Environment
   - Browser: [e.g. Chrome 120]
   - OS: [e.g. Windows 11]
   - Device: [e.g. Desktop]
   - GrowKitty Version: [e.g. 1.0.0]
   
   ## Additional Context
   Any other relevant information.
   
   ## Possible Solution (optional)
   Ideas for fixing the issue.

Feature Requests
~~~~~~~~~~~~~~~~

Use this template:

.. code-block:: markdown

   ## Feature Description
   Clear description of the proposed feature.
   
   ## Problem to Solve
   What problem does this feature address?
   
   ## Proposed Solution
   How should this feature work?
   
   ## Alternatives Considered
   Other approaches you've thought about.
   
   ## Additional Context
   Mockups, examples, or related features.
   
   ## Would you like to implement this?
   - [ ] Yes, I can work on this
   - [ ] No, just suggesting

Testing Guidelines
------------------

Manual Testing
~~~~~~~~~~~~~~

Before submitting, test:

**Basic Functionality**

- [ ] Create new habit
- [ ] Complete habit
- [ ] Skip habit
- [ ] Delete habit
- [ ] View statistics

**Edge Cases**

- [ ] Midnight rollover
- [ ] Timezone changes
- [ ] Offline usage
- [ ] Storage limits
- [ ] Long habit names

**Cross-Browser**

- [ ] Chrome
- [ ] Firefox
- [ ] Safari
- [ ] Edge

**Mobile Testing**

- [ ] Responsive layout
- [ ] Touch interactions
- [ ] Install as PWA
- [ ] Notifications

Automated Testing (Future)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

When available:

.. code-block:: bash

   # Run all tests
   npm test
   
   # Run specific test file
   npm test habits.test.js
   
   # Run with coverage
   npm test -- --coverage

Documentation Contributions
---------------------------

Documentation Standards
~~~~~~~~~~~~~~~~~~~~~~~

**Writing Style**

- Clear and concise
- Active voice
- Present tense
- Second person ("you")
- Short sentences

**Structure**

- Logical organization
- Progressive complexity
- Clear headings
- Code examples
- Visual aids

**Formatting**

- Use reStructuredText (RST)
- Consistent indentation
- Code blocks with language
- Proper cross-references

**Example:**

.. code-block:: rst

   Feature Name
   ============
   
   Brief introduction to the feature.
   
   Overview
   --------
   
   Detailed explanation with context.
   
   Usage
   -----
   
   How to use the feature:
   
   1. First step
   2. Second step
   3. Third step
   
   **Example:**
   
   .. code-block:: javascript
   
      // Code example here
      const example = new Feature();
      example.use();
   
   See Also
   --------
   
   - :doc:`related-doc`
   - :doc:`another-doc`

Building Documentation
~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

   # Install Sphinx
   pip install -r docs/requirements.txt
   
   # Build HTML docs
   cd docs
   make html
   
   # View locally
   open _build/html/index.html

Translation
~~~~~~~~~~~

To translate documentation:

1. Create new language directory: ``docs/locales/ko/``
2. Copy RST files from ``docs/``
3. Translate content
4. Update ``docs/conf.py`` with language
5. Submit PR with translations

Community Guidelines
--------------------

Code of Conduct
~~~~~~~~~~~~~~~

**Our Pledge**

We pledge to make participation in our project a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity, level of experience, nationality, personal appearance, race, religion, or sexual identity and orientation.

**Our Standards**

Examples of behavior that contributes to creating a positive environment:

- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards others

Examples of unacceptable behavior:

- Trolling, insulting/derogatory comments, and personal attacks
- Public or private harassment
- Publishing others' private information without permission
- Other conduct which could reasonably be considered inappropriate

Communication Channels
~~~~~~~~~~~~~~~~~~~~~~

- **GitHub Issues**: Bug reports and feature requests
- **GitHub Discussions**: General questions and ideas
- **Pull Requests**: Code contributions and reviews
- **Email**: For private matters (contact maintainers)

Getting Help
~~~~~~~~~~~~

If you need help:

1. Check existing documentation
2. Search closed issues
3. Ask in GitHub Discussions
4. Open a new issue if needed

Recognition
-----------

Contributors
~~~~~~~~~~~~

All contributors are recognized in:

- README.md contributors section
- Release notes
- About page in the app
- Annual contributor highlights

Types of Recognition
~~~~~~~~~~~~~~~~~~~~

- **Code Contributors**: For code commits
- **Documentation Contributors**: For docs improvements
- **Community Contributors**: For support and engagement
- **Design Contributors**: For visual assets
- **Translation Contributors**: For localization

Thank You
---------

Thank you for contributing to GrowKitty! Your efforts help make this project better for everyone. Every contribution, no matter how small, is valued and appreciated.

Questions?
----------

If you have questions about contributing:

- Read through this guide again
- Check the :doc:`technical-overview`
- Ask in GitHub Discussions
- Open an issue with the "question" label

Happy contributing! 🐱