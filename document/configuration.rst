Configuration Guide
===================

This guide explains how to customize GrowKitty to match your preferences and workflow.

Settings Overview
-----------------

Access settings by clicking the ⚙️ icon in the top-right corner of the dashboard.

General Settings
----------------

Profile Settings
~~~~~~~~~~~~~~~~

**Username**

- Your display name in the app
- Shown on leaderboards (if enabled)
- Max 20 characters

**Cat Name**

- Your virtual cat's name
- Can be changed anytime
- Max 20 characters

**Language**

Available languages:

- English (en)
- Korean (ko)
- Japanese (ja)
- Spanish (es)
- French (fr)
- German (de)

**Time Zone**

- Auto-detected by default
- Can be manually set
- Affects daily reset time and reminders

Display Settings
~~~~~~~~~~~~~~~~

**Theme**

Choose your preferred visual theme:

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Theme
     - Description
   * - Light Mode
     - Bright, clean interface (default)
   * - Dark Mode
     - Easy on eyes in low light
   * - Auto
     - Switches based on system preference
   * - Cozy Mode
     - Warm, comfortable colors
   * - High Contrast
     - Enhanced visibility

**Color Scheme**

Accent color options:

- Blue (default)
- Green
- Purple
- Pink
- Orange
- Red

**Font Size**

- Small
- Medium (default)
- Large
- Extra Large

**Animations**

- None (fastest performance)
- Reduced (some animations)
- Normal (default)
- Enhanced (full animations)

Habit Settings
--------------

Default Habit Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Set defaults for new habits:

.. code-block:: javascript

   {
     "frequency": "daily",        // daily, weekly, custom
     "reminderEnabled": true,
     "reminderTime": "09:00",
     "category": "general",
     "trackNotes": false,
     "requireConfirmation": false
   }

Habit Categories
~~~~~~~~~~~~~~~~

Manage habit categories:

**Default Categories**

- Health & Fitness (🏃)
- Productivity (💼)
- Learning (📚)
- Mindfulness (🧘)
- Creativity (🎨)
- Household (🏠)
- Finance (💰)
- Social (👥)

**Adding Custom Categories**

1. Settings → Habit Categories
2. Click "+ Add Category"
3. Enter:

   - Name
   - Emoji icon
   - Color
   - Sort order

4. Click "Save"

**Editing Categories**

- Click category to edit
- Change name, icon, or color
- Reorder by drag-and-drop
- Delete unused categories

Completion Settings
~~~~~~~~~~~~~~~~~~~

**Confirmation Mode**

- None: Instant check-off
- Single tap: Click once to mark complete
- Double tap: Click twice to confirm
- Swipe: Swipe gesture to complete (mobile)

**Undo Window**

Time to undo accidental completions:

- 5 seconds
- 15 seconds (default)
- 30 seconds
- 1 minute
- Disabled

**Retroactive Completion**

Allow marking habits complete for past dates:

- Enabled: Can complete for any past date
- Last 7 days: Only recent week
- Yesterday only: Just previous day
- Disabled: Today only

Streak Settings
~~~~~~~~~~~~~~~

**Streak Freeze**

Protection against breaking streaks:

.. code-block:: text

   Automatic: Apply when forgetting a day
   Manual: Must activate before missing
   Disabled: No streak protection

**Streak Start Day**

- Any day (default)
- Monday (week-based)
- Custom day

**Grace Period**

Extra time to complete daily habits:

- None: Must complete before midnight
- 2 hours: Until 2 AM
- 4 hours: Until 4 AM (default)
- 6 hours: Until 6 AM

Mission Settings
----------------

Mission Preferences
~~~~~~~~~~~~~~~~~~~

**Daily Mission Count**

Number of missions per day:

- 2 missions
- 3 missions (default)
- 4 missions
- 5 missions

**Mission Difficulty**

- Easy: Simple, achievable goals
- Medium: Balanced challenge (default)
- Hard: Ambitious targets
- Mixed: Variety of difficulties

**Mission Types**

Enable/disable specific mission types:

.. list-table::
   :header-rows: 1
   :widths: 40 15 45

   * - Mission Type
     - Default
     - Description
   * - Completion Count
     - ✅
     - Complete X habits today
   * - Category Focus
     - ✅
     - Complete all habits in category
   * - Early Bird
     - ✅
     - Complete habits before time
   * - Perfect Day
     - ✅
     - 100% completion rate
   * - Streak Milestone
     - ✅
     - Reach streak goal
   * - Social Challenge
     - ⬜
     - Interact with community
   * - Exploration
     - ⬜
     - Try new features

**Mission Refresh**

- Auto-refresh: Daily at midnight
- Manual only: Must use refresh button
- Keep incomplete: Carry over to next day

Notification Settings
---------------------

Habit Reminders
~~~~~~~~~~~~~~~

**Reminder Timing**

Per-habit reminder configuration:

- Exact time: At specified time
- 5 minutes before: Early reminder
- 15 minutes before: Advanced notice
- 30 minutes before: Extra preparation
- Custom: Set your own offset

**Reminder Repeat**

If not completed:

- No repeat: Single notification
- Every 30 minutes: Regular nudges
- Every hour: Periodic reminders
- Every 3 hours: Occasional check-ins

**Quiet Hours**

Disable notifications during:

.. code-block:: text

   Start: 22:00 (10 PM)
   End: 07:00 (7 AM)
   
   Days: Weekdays only / All days / Custom

System Notifications
~~~~~~~~~~~~~~~~~~~~

Enable/disable notification types:

.. list-table::
   :header-rows: 1
   :widths: 40 15 45

   * - Notification Type
     - Default
     - Description
   * - Habit Reminders
     - ✅
     - Scheduled habit alerts
   * - Mission Available
     - ✅
     - New daily missions
   * - Mission Complete
     - ✅
     - Mission completion
   * - Level Up
     - ✅
     - User level increase
   * - Cat Mood Change
     - ⬜
     - Cat state updates
   * - Streak Milestone
     - ✅
     - Streak achievements
   * - Daily Summary
     - ⬜
     - End-of-day report
   * - Weekly Report
     - ⬜
     - Weekly statistics

**Notification Sound**

- System default
- Cat meow
- Gentle chime
- Digital beep
- None (silent)

**Notification Badge**

- Show count on app icon
- Enabled / Disabled

Cat Settings
------------

Cat Customization
~~~~~~~~~~~~~~~~~

**Cat Personality**

Affects reaction animations:

- Playful: Energetic and bouncy
- Calm: Gentle and relaxed
- Curious: Investigative behavior
- Sleepy: Lazy animations
- Mischievous: Playful pranks

**Animation Speed**

- Slow: 0.5x speed
- Normal: 1.0x speed (default)
- Fast: 1.5x speed
- Very Fast: 2.0x speed

**Auto-play Animations**

- Always: Continuous animations
- On interaction: Only when clicked
- On events: Habit/mission completion
- Never: Static display

Growth Settings
~~~~~~~~~~~~~~~

**Growth Rate**

Speed of cat evolution:

- Slow: More time per stage
- Normal: Balanced progression (default)
- Fast: Quick evolution
- Custom: Set XP requirements

**Mood Sensitivity**

How quickly mood changes:

- Low: Stable, gradual changes
- Medium: Balanced response (default)
- High: Reactive to each action

Privacy & Security
------------------

Data Privacy
~~~~~~~~~~~~

**Profile Visibility**

- Public: Anyone can view
- Friends only: Limited visibility
- Private: Hidden from all (default)

**Leaderboard Participation**

- Opt-in: Show on leaderboards
- Opt-out: Hidden from rankings (default)
- Anonymous: Show without username

**Share History**

- Keep share history
- Auto-delete after 30 days
- Don't track shares

Data Management
~~~~~~~~~~~~~~~

**Auto-save**

- Every change: Instant saving
- Every 5 minutes: Periodic saves (default)
- Manual only: Click to save

**Backup Frequency**

Automatic local backups:

- Daily
- Weekly (default)
- Monthly
- Disabled

**Storage Usage**

View and manage data:

.. code-block:: text

   Habits: 245 KB
   Completions: 1.8 MB
   Cat data: 156 KB
   Settings: 12 KB
   
   Total: 2.2 MB / 10 MB available

**Data Export**

1. Settings → Data Management
2. Click "Export Data"
3. Choose format:

   - JSON (full data)
   - CSV (habit log)
   - PDF (report)

4. Select date range
5. Download file

**Data Import**

1. Settings → Data Management
2. Click "Import Data"
3. Select file
4. Choose merge or replace
5. Confirm import

**Clear All Data**

Permanently delete everything:

1. Settings → Data Management
2. Click "Clear All Data"
3. Enter confirmation code
4. Confirm deletion

Advanced Settings
-----------------

Developer Options
~~~~~~~~~~~~~~~~~

**Debug Mode**

Enable logging and diagnostics:

- Show console logs
- Display performance metrics
- Enable dev tools
- Export debug report

**Experimental Features**

Opt into beta features:

- AI habit suggestions
- Advanced analytics
- Social features
- Voice commands

**API Access**

For integration with other apps:

1. Generate API key
2. Set permissions
3. Configure webhooks
4. Test connection

Custom CSS
~~~~~~~~~~

Apply custom styling:

.. code-block:: css

   /* Custom theme example */
   :root {
     --primary-color: #8B5CF6;
     --background-color: #F9FAFB;
     --text-color: #1F2937;
     --border-radius: 12px;
   }
   
   .habit-card {
     box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
   }

1. Settings → Advanced → Custom CSS
2. Paste your CSS code
3. Preview changes
4. Save and apply

Configuration File
------------------

For power users, directly edit config:

Location
~~~~~~~~

Config stored in LocalStorage:

.. code-block:: javascript

   localStorage.getItem('growkitty_config')

Format
~~~~~~

JSON configuration structure:

.. code-block:: json

   {
     "version": "1.0.0",
     "user": {
       "username": "YourName",
       "timezone": "Asia/Seoul",
       "language": "en"
     },
     "display": {
       "theme": "dark",
       "colorScheme": "purple",
       "fontSize": "medium",
       "animations": "normal"
     },
     "habits": {
       "defaultFrequency": "daily",
       "reminderEnabled": true,
       "gracePerio dHours": 4,
       "allowRetroactive": true
     },
     "missions": {
       "dailyCount": 3,
       "difficulty": "medium",
       "autoRefresh": true
     },
     "notifications": {
       "enabled": true,
       "sound": "cat_meow",
       "quietHoursStart": "22:00",
       "quietHoursEnd": "07:00"
     },
     "cat": {
       "personality": "playful",
       "animationSpeed": 1.0,
       "autoplay": true
     },
     "privacy": {
       "profileVisibility": "private",
       "leaderboardParticipation": false
     }
   }

Editing
~~~~~~~

1. Export current config
2. Edit JSON file
3. Validate JSON syntax
4. Import modified config
5. Restart application

Reset to Defaults
~~~~~~~~~~~~~~~~~

Restore original settings:

1. Settings → Advanced
2. Click "Reset to Defaults"
3. Choose what to reset:

   - All settings
   - Display only
   - Habits only
   - Notifications only

4. Confirm reset

Tips & Recommendations
----------------------

Best Practices
~~~~~~~~~~~~~~

**For Beginners**

- Start with 3-5 habits
- Enable reminders
- Use normal difficulty missions
- Keep animations enabled

**For Productivity**

- Disable non-essential notifications
- Use category focus
- Enable streak freeze
- Set morning reminders

**For Gamification**

- Enable all mission types
- Join leaderboards
- Share achievements
- Collect accessories

**For Privacy**

- Use private profile
- Disable sharing
- Opt out of leaderboards
- Regular data exports

Platform-Specific
~~~~~~~~~~~~~~~~~

**Mobile Users**

- Enable push notifications
- Use swipe gestures
- Reduce animations
- Install as PWA

**Desktop Users**

- Use keyboard shortcuts
- Multiple windows
- Enhanced animations
- Larger font size

Troubleshooting Config
----------------------

Common Issues
~~~~~~~~~~~~~

**Settings Not Saving**

- Check browser storage permissions
- Verify LocalStorage is enabled
- Clear cache and retry
- Export/import config

**Notifications Not Working**

- Grant browser permissions
- Check system notification settings
- Verify quiet hours
- Test with simple notification

**Performance Issues**

- Reduce animations
- Disable auto-play
- Lower mission count
- Clear old data

Next Steps
----------

- :doc:`usage` - Learn to use configured features
- :doc:`troubleshooting` - Solve common problems
- :doc:`faq` - Find quick answers