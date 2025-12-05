Technical Overview
==================

This document provides a comprehensive technical overview of GrowKitty's architecture, components, and implementation details.

Architecture
------------

System Design
~~~~~~~~~~~~~

GrowKitty follows a client-side architecture pattern:

.. code-block:: text

   ┌─────────────────────────────────────────┐
   │          User Interface (UI)            │
   │     HTML5 + CSS3 + JavaScript (ES6)     │
   └─────────────────────────────────────────┘
                     │
                     ▼
   ┌─────────────────────────────────────────┐
   │       Application Logic Layer           │
   │  ├─ Habit Manager                       │
   │  ├─ Mission System                      │
   │  ├─ Cat Behavior Engine                 │
   │  ├─ Reward Calculator                   │
   │  └─ Analytics Tracker                   │
   └─────────────────────────────────────────┘
                     │
                     ▼
   ┌─────────────────────────────────────────┐
   │         Data Persistence Layer          │
   │      Browser LocalStorage (JSON)        │
   └─────────────────────────────────────────┘

Design Patterns
~~~~~~~~~~~~~~~

**Module Pattern**

Each feature is encapsulated in its own module:

.. code-block:: javascript

   const HabitManager = (function() {
     // Private variables and methods
     let habits = [];
     
     function saveToStorage() { /* ... */ }
     
     // Public API
     return {
       addHabit: function(habit) { /* ... */ },
       removeHabit: function(id) { /* ... */ },
       getHabits: function() { return habits; }
     };
   })();

**Observer Pattern**

Event-driven updates for reactive UI:

.. code-block:: javascript

   class EventEmitter {
     constructor() {
       this.events = {};
     }
     
     on(event, listener) {
       if (!this.events[event]) {
         this.events[event] = [];
       }
       this.events[event].push(listener);
     }
     
     emit(event, data) {
       if (this.events[event]) {
         this.events[event].forEach(listener => listener(data));
       }
     }
   }

**State Management**

Centralized application state:

.. code-block:: javascript

   const AppState = {
     user: {
       username: '',
       level: 1,
       xp: 0,
       coins: 0
     },
     cat: {
       name: '',
       stage: 'kitten',
       mood: 'happy',
       accessories: []
     },
     habits: [],
     missions: [],
     settings: {}
   };

Core Components
---------------

1. Habit Management System
~~~~~~~~~~~~~~~~~~~~~~~~~~~

**File**: ``js/habits.js``

Handles all habit-related operations:

.. code-block:: javascript

   class Habit {
     constructor(config) {
       this.id = generateId();
       this.name = config.name;
       this.category = config.category;
       this.frequency = config.frequency; // 'daily', 'weekly', 'custom'
       this.completions = [];
       this.streak = 0;
       this.createdAt = new Date();
     }
     
     complete(date = new Date()) {
       this.completions.push({
         date: date,
         timestamp: Date.now(),
         notes: ''
       });
       this.updateStreak();
       EventBus.emit('habit:completed', this);
     }
     
     updateStreak() {
       // Calculate current streak
       const sorted = this.completions.sort((a, b) => b.date - a.date);
       let streak = 0;
       let checkDate = new Date();
       
       for (let completion of sorted) {
         if (isSameDay(completion.date, checkDate)) {
           streak++;
           checkDate.setDate(checkDate.getDate() - 1);
         } else {
           break;
         }
       }
       
       this.streak = streak;
     }
     
     getSuccessRate(days = 30) {
       const recent = this.completions.filter(c => 
         Date.now() - c.timestamp < days * 24 * 60 * 60 * 1000
       );
       return (recent.length / days) * 100;
     }
   }

**Key Functions**

- ``addHabit(config)``: Create new habit
- ``editHabit(id, updates)``: Modify existing habit
- ``deleteHabit(id)``: Remove habit
- ``completeHabit(id, date)``: Mark as complete
- ``skipHabit(id, reason)``: Skip with note
- ``getHabitStats(id)``: Calculate statistics

2. Mission Generation System
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**File**: ``js/missions.js``

Generates and manages daily missions:

.. code-block:: javascript

   class MissionGenerator {
     constructor(habits) {
       this.habits = habits;
       this.missionTemplates = [
         {
           type: 'completion_count',
           title: 'Complete {count} habits today',
           requirement: (count) => ({ completed: 0, target: count }),
           reward: { xp: 100, coins: 20 }
         },
         {
           type: 'category_focus',
           title: 'Complete all {category} habits',
           requirement: (category) => ({ category: category }),
           reward: { xp: 150, coins: 30 }
         },
         {
           type: 'early_bird',
           title: 'Complete 3 habits before 10 AM',
           requirement: () => ({ time: '10:00', count: 3 }),
           reward: { xp: 200, coins: 40 }
         }
       ];
     }
     
     generateDailyMissions(count = 3) {
       const missions = [];
       const templates = this.shuffleArray([...this.missionTemplates]);
       
       for (let i = 0; i < count; i++) {
         const template = templates[i];
         const mission = this.createMission(template);
         missions.push(mission);
       }
       
       return missions;
     }
     
     createMission(template) {
       return {
         id: generateId(),
         type: template.type,
         title: this.populateTitle(template.title),
         description: template.description,
         requirement: template.requirement(),
         reward: template.reward,
         progress: 0,
         completed: false,
         expiresAt: this.getEndOfDay()
       };
     }
     
     checkMissionProgress(mission, habits) {
       switch (mission.type) {
         case 'completion_count':
           const completed = habits.filter(h => 
             h.isCompletedToday()
           ).length;
           mission.progress = completed / mission.requirement.target;
           break;
         // ... other mission types
       }
       
       if (mission.progress >= 1 && !mission.completed) {
         this.completeMission(mission);
       }
     }
   }

3. Virtual Cat Behavior Engine
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**File**: ``js/cat.js``

Controls cat appearance, mood, and animations:

.. code-block:: javascript

   class VirtualCat {
     constructor(name) {
       this.name = name;
       this.stage = 'kitten'; // kitten, young, adult, master, legendary
       this.level = 1;
       this.mood = 'happy'; // happy, content, neutral, sad, sick
       this.happiness = 100;
       this.accessories = [];
       this.animations = new AnimationController();
     }
     
     updateMood(successRate) {
       if (successRate >= 80) {
         this.mood = 'happy';
         this.happiness = 100;
       } else if (successRate >= 60) {
         this.mood = 'content';
         this.happiness = 75;
       } else if (successRate >= 40) {
         this.mood = 'neutral';
         this.happiness = 50;
       } else if (successRate >= 20) {
         this.mood = 'sad';
         this.happiness = 25;
       } else {
         this.mood = 'sick';
         this.happiness = 10;
       }
       
       this.updateAppearance();
     }
     
     grow(xp) {
       this.level += Math.floor(xp / 100);
       
       if (this.level >= 51) this.stage = 'legendary';
       else if (this.level >= 31) this.stage = 'master';
       else if (this.level >= 16) this.stage = 'adult';
       else if (this.level >= 6) this.stage = 'young';
       
       this.updateAppearance();
     }
     
     react(event) {
       const reactions = {
         'habit_completed': 'celebrate',
         'habit_skipped': 'disappointed',
         'mission_completed': 'excited',
         'leveled_up': 'proud',
         'petted': 'purr'
       };
       
       const animation = reactions[event] || 'idle';
       this.animations.play(animation);
     }
     
     equipAccessory(item) {
       const slot = item.slot; // hat, clothes, accessory
       
       // Remove existing item in slot
       this.accessories = this.accessories.filter(a => a.slot !== slot);
       
       // Add new item
       this.accessories.push(item);
       this.updateAppearance();
     }
     
     updateAppearance() {
       // Render cat with current stage, mood, and accessories
       Renderer.renderCat({
         stage: this.stage,
         mood: this.mood,
         accessories: this.accessories,
         animation: this.animations.current
       });
     }
   }

4. Reward System
~~~~~~~~~~~~~~~~

**File**: ``js/rewards.js``

Calculates and distributes rewards:

.. code-block:: javascript

   class RewardSystem {
     constructor() {
       this.baseRewards = {
         habitComplete: { xp: 10, coins: 5 },
         missionComplete: { xp: 100, coins: 20 },
         dailyStreak: { xp: 50, coins: 10 },
         levelUp: { gems: 1 }
       };
     }
     
     calculateReward(action, multiplier = 1) {
       const base = this.baseRewards[action];
       
       return {
         xp: Math.floor(base.xp * multiplier),
         coins: Math.floor(base.coins * multiplier),
         gems: base.gems || 0
       };
     }
     
     applyStreak Bonus(streak) {
       if (streak >= 30) return 3.0;
       if (streak >= 14) return 2.0;
       if (streak >= 7) return 1.5;
       return 1.0;
     }
     
     grantReward(user, reward, source) {
       user.xp += reward.xp;
       user.coins += reward.coins;
       user.gems += reward.gems || 0;
       
       // Check for level up
       const newLevel = Math.floor(user.xp / 100) + 1;
       if (newLevel > user.level) {
         this.levelUp(user, newLevel);
       }
       
       // Log transaction
       this.logTransaction({
         type: 'earned',
         source: source,
         amount: reward,
         timestamp: Date.now()
       });
       
       // Update UI
       EventBus.emit('reward:granted', reward);
     }
     
     levelUp(user, newLevel) {
       user.level = newLevel;
       const levelReward = this.calculateReward('levelUp');
       user.gems += levelReward.gems;
       
       EventBus.emit('user:levelup', { level: newLevel });
     }
   }

5. Data Persistence
~~~~~~~~~~~~~~~~~~~

**File**: ``js/storage.js``

Manages browser LocalStorage:

.. code-block:: javascript

   class StorageManager {
     constructor() {
       this.storageKey = 'growkitty_data';
       this.version = '1.0.0';
     }
     
     save(data) {
       try {
         const serialized = JSON.stringify({
           version: this.version,
           timestamp: Date.now(),
           data: data
         });
         
         localStorage.setItem(this.storageKey, serialized);
         return true;
       } catch (error) {
         console.error('Storage save failed:', error);
         return false;
       }
     }
     
     load() {
       try {
         const serialized = localStorage.getItem(this.storageKey);
         
         if (!serialized) {
           return this.getDefaultState();
         }
         
         const parsed = JSON.parse(serialized);
         
         // Version migration if needed
         if (parsed.version !== this.version) {
           return this.migrate(parsed);
         }
         
         return parsed.data;
       } catch (error) {
         console.error('Storage load failed:', error);
         return this.getDefaultState();
       }
     }
     
     clear() {
       localStorage.removeItem(this.storageKey);
     }
     
     export(format = 'json') {
       const data = this.load();
       
       if (format === 'json') {
         return JSON.stringify(data, null, 2);
       } else if (format === 'csv') {
         return this.convertToCSV(data);
       }
     }
     
     import(serialized, format = 'json') {
       try {
         let data;
         
         if (format === 'json') {
           data = JSON.parse(serialized);
         } else if (format === 'csv') {
           data = this.parseCSV(serialized);
         }
         
         return this.save(data);
       } catch (error) {
         console.error('Import failed:', error);
         return false;
       }
     }
   }

Technology Stack
----------------

Frontend Technologies
~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 20 50

   * - Technology
     - Version
     - Purpose
   * - HTML5
     - 5.2
     - Semantic markup structure
   * - CSS3
     - 3.0
     - Styling, animations, responsive design
   * - JavaScript (ES6+)
     - ECMAScript 2015+
     - Application logic and interactivity
   * - LocalStorage API
     - Web Storage
     - Client-side data persistence
   * - Canvas API
     - HTML5
     - Cat animations and effects
   * - Service Workers
     - (Optional)
     - Offline functionality (PWA)

Development Tools
~~~~~~~~~~~~~~~~~

- **Version Control**: Git 2.x
- **Code Editor**: VS Code (recommended)
- **Browser DevTools**: Chrome/Firefox Developer Tools
- **Linting**: ESLint with Airbnb config
- **Formatting**: Prettier
- **Testing**: Jest (unit tests)

Build & Deployment
~~~~~~~~~~~~~~~~~~

No build process required - pure vanilla JavaScript:

- **Development**: Local server (Python, Node.js, or VS Code Live Server)
- **Production**: Static hosting (GitHub Pages, Netlify, Vercel)
- **CI/CD**: GitHub Actions (optional)

Performance Optimizations
-------------------------

Loading Performance
~~~~~~~~~~~~~~~~~~~

**Strategies**

- Lazy loading for images
- Deferred JavaScript loading
- Minified CSS/JS in production
- Service Worker caching

.. code-block:: javascript

   // Lazy load images
   const imageObserver = new IntersectionObserver((entries) => {
     entries.forEach(entry => {
       if (entry.isIntersecting) {
         const img = entry.target;
         img.src = img.dataset.src;
         imageObserver.unobserve(img);
       }
     });
   });

Runtime Performance
~~~~~~~~~~~~~~~~~~~

**Optimization Techniques**

- Debounced event handlers
- RequestAnimationFrame for animations
- Virtual scrolling for long lists
- Efficient DOM manipulation

.. code-block:: javascript

   // Debounce function
   function debounce(func, wait) {
     let timeout;
     return function executedFunction(...args) {
       const later = () => {
         clearTimeout(timeout);
         func(...args);
       };
       clearTimeout(timeout);
       timeout = setTimeout(later, wait);
     };
   }
   
   // Use for search input
   const handleSearch = debounce((query) => {
     // Search logic
   }, 300);

Storage Optimization
~~~~~~~~~~~~~~~~~~~~

- Compression for large data
- Periodic cleanup of old data
- Incremental saves
- Storage quota monitoring

Security Considerations
-----------------------

Data Privacy
~~~~~~~~~~~~

- All data stored locally in browser
- No server-side storage or transmission
- No user tracking or analytics
- Export/delete options available

Input Validation
~~~~~~~~~~~~~~~~

.. code-block:: javascript

   function validateHabitInput(input) {
     const errors = [];
     
     if (!input.name || input.name.trim().length === 0) {
       errors.push('Habit name is required');
     }
     
     if (input.name.length > 100) {
       errors.push('Habit name must be under 100 characters');
     }
     
     if (!['daily', 'weekly', 'custom'].includes(input.frequency)) {
       errors.push('Invalid frequency');
     }
     
     return {
       valid: errors.length === 0,
       errors: errors
     };
   }

XSS Prevention
~~~~~~~~~~~~~~

.. code-block:: javascript

   function sanitizeHTML(html) {
     const temp = document.createElement('div');
     temp.textContent = html;
     return temp.innerHTML;
   }
   
   // Use when rendering user input
   element.innerHTML = sanitizeHTML(userInput);

Testing Strategy
----------------

Unit Tests
~~~~~~~~~~

Test individual components:

.. code-block:: javascript

   describe('Habit', () => {
     test('calculates streak correctly', () => {
       const habit = new Habit({ name: 'Test' });
       habit.complete(new Date('2025-01-01'));
       habit.complete(new Date('2025-01-02'));
       habit.complete(new Date('2025-01-03'));
       
       expect(habit.streak).toBe(3);
     });
   });

Integration Tests
~~~~~~~~~~~~~~~~~

Test component interactions:

.. code-block:: javascript

   describe('Habit + Rewards', () => {
     test('completing habit grants rewards', () => {
       const habit = new Habit({ name: 'Test' });
       const user = { xp: 0, coins: 0 };
       
       habit.complete();
       RewardSystem.grantReward(user, 'habitComplete');
       
       expect(user.xp).toBe(10);
       expect(user.coins).toBe(5);
     });
   });

Browser Compatibility
---------------------

Supported Features
~~~~~~~~~~~~~~~~~~

The app uses modern web APIs:

- **ES6+ JavaScript**: Arrow functions, classes, modules
- **CSS Grid & Flexbox**: Layout system
- **LocalStorage**: Data persistence
- **Canvas**: Graphics rendering
- **Intersection Observer**: Lazy loading

Polyfills
~~~~~~~~~

For older browsers, include:

.. code-block:: html

   <!-- Polyfill for older browsers -->
   <script src="https://cdn.polyfill.io/v3/polyfill.min.js"></script>

Contributing to Development
---------------------------

For developers interested in contributing, see:

- :doc:`contributing` - Contribution guidelines
- `GitHub Repository <https://github.com/lillian-na/GrowKitty>`_ - Source code
- `Issue Tracker <https://github.com/lillian-na/GrowKitty/issues>`_ - Bug reports and features