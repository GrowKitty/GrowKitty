Frequently Asked Questions
==========================

Find quick answers to common questions about GrowKitty.

General Questions
-----------------

What is GrowKitty?
~~~~~~~~~~~~~~~~~~

GrowKitty is an open-source habit-tracking application that uses gamification to help you build and maintain healthy habits. Your virtual cat companion grows and reacts based on your habit completion rate, making habit formation more engaging and fun.

Is GrowKitty free?
~~~~~~~~~~~~~~~~~~

Yes! GrowKitty is completely free and open-source under the MIT License. There are no subscriptions, in-app purchases, or hidden costs.

Do I need to create an account?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No. GrowKitty runs entirely in your browser and stores all data locally on your device. No account, registration, or server connection is required.

Is my data private?
~~~~~~~~~~~~~~~~~~~

Yes, completely. All your habit data is stored locally in your browser's LocalStorage. Nothing is sent to external servers, and no one can access your data except you.

Which devices can I use GrowKitty on?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

GrowKitty works on any device with a modern web browser:

- Desktop computers (Windows, Mac, Linux)
- Laptops
- Tablets
- Smartphones
- Any device with Chrome, Firefox, Safari, or Edge

Can I use GrowKitty offline?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! Once loaded, GrowKitty works completely offline. Your data is stored locally, so you can track habits without an internet connection.

Getting Started
---------------

How do I install GrowKitty?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Option 1: Direct Use**

1. Visit the GrowKitty website or download from GitHub
2. Open ``index.html`` in your browser
3. Start tracking habits immediately

**Option 2: Install as App (PWA)**

Mobile:

1. Open GrowKitty in browser
2. Tap browser menu
3. Select "Add to Home Screen"
4. GrowKitty appears like a native app

Desktop (Chrome):

1. Visit GrowKitty
2. Look for install icon in address bar
3. Click "Install"

See :doc:`getting-started` for detailed instructions.

How do I create my first habit?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Click the "+ Add Habit" button
2. Enter habit name (e.g., "Morning Exercise")
3. Select category and frequency
4. Set reminder time (optional)
5. Click "Save Habit"

What's the best number of habits to start with?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Start with 3-5 habits. This is manageable without being overwhelming. You can always add more later as these become routine.

Using GrowKitty
---------------

How do I mark a habit as complete?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Quick Method:**

Click the checkbox next to the habit name.

**Detailed Method:**

1. Click the habit card
2. Add notes (optional)
3. Click "Mark Complete"

Can I complete habits for previous days?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, if enabled in settings:

1. Settings → Habits → Retroactive Completion
2. Select allowed timeframe
3. Click habit → Complete for specific date

How do missions work?
~~~~~~~~~~~~~~~~~~~~~~

Missions are daily challenges that:

1. Generate automatically each day
2. Provide variety to prevent monotony
3. Offer bonus rewards (XP, coins)
4. Update progress automatically

Complete mission requirements to earn rewards!

What happens if I skip a day?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Immediate Effects:**

- Habit streak resets to 0
- Cat's mood may decrease
- Success rate drops

**Recovery Options:**

- Use a Streak Freeze (if available)
- Resume next day to rebuild streak
- Your cat will recover as you complete habits

Can I pause or delete habits?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Pause:**

Click habit → "Archive" to pause without deleting. Archived habits don't affect statistics but remain accessible.

**Delete:**

Click habit → "Delete" → Confirm. This permanently removes the habit and its history.

Virtual Cat
-----------

How does my cat grow?
~~~~~~~~~~~~~~~~~~~~~~

Your cat grows based on:

- **Experience Points (XP)**: Earned from completing habits and missions
- **Consistency**: Higher success rates accelerate growth
- **Time**: Reaching level milestones triggers growth stages

**Growth Stages:**

1. Kitten (Level 1-5)
2. Young Cat (Level 6-15)
3. Adult Cat (Level 16-30)
4. Master Cat (Level 31-50)
5. Legendary Cat (Level 51+)

Why is my cat sad?
~~~~~~~~~~~~~~~~~~

Your cat's mood reflects your recent habit completion rate:

- **Happy**: 80%+ completion rate
- **Content**: 60-79% completion
- **Neutral**: 40-59% completion
- **Sad**: 20-39% completion
- **Sick**: Below 20% completion

To improve your cat's mood, complete more habits consistently!

How do I get cat accessories?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Earn Through:**

- Completing missions
- Reaching level milestones
- Achieving streaks
- Special events

**Purchase With:**

- Coins: Earned daily
- Gems: Rare currency from leveling up

Shop → Browse → Select → Equip

Can I change my cat's name?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! Settings → Cat → Cat Name → Enter new name → Save

Data & Privacy
--------------

Where is my data stored?
~~~~~~~~~~~~~~~~~~~~~~~~~

All data is stored in your browser's LocalStorage on your device. Nothing is uploaded to cloud servers or external databases.

Can I export my data?
~~~~~~~~~~~~~~~~~~~~~

Yes:

1. Settings → Data Management
2. Click "Export Data"
3. Choose format (JSON, CSV, PDF)
4. Select date range
5. Download file

Keep backups for safety!

Can I sync across devices?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currently, GrowKitty doesn't have built-in sync. However, you can:

1. Export data from Device A
2. Transfer file to Device B
3. Import data on Device B

**Tip:** Use cloud storage (Dropbox, Google Drive) to share the export file between devices.

What happens if I clear my browser data?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**If you clear browser data (cache, cookies, site data):**

- **All GrowKitty data will be deleted**
- Habits, completions, and progress lost
- Cat and customization reset

**Prevention:**

- Export data regularly
- Keep backups
- Be careful with browser cleaning tools

How do I transfer data to a new device?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. **On old device:**

   - Settings → Export Data
   - Save the JSON file

2. **On new device:**

   - Open GrowKitty
   - Settings → Import Data
   - Select the exported file
   - Confirm import

Can I recover deleted data?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unfortunately, no. Once data is deleted or browser storage is cleared, it cannot be recovered unless you have a backup export.

**Best Practice:** Export your data weekly or monthly for safety.

Troubleshooting
---------------

Why isn't GrowKitty loading?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Quick Fixes:**

1. Clear browser cache (Ctrl+Shift+Del)
2. Try incognito/private mode
3. Check browser console (F12) for errors
4. Update browser to latest version
5. Try different browser

See :doc:`troubleshooting` for detailed solutions.

Why aren't my changes saving?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Common Causes:**

- Browser privacy settings blocking LocalStorage
- Incognito/private browsing mode
- Storage quota exceeded
- Browser extension interfering

**Solutions:**

1. Check Settings → Privacy → Allow site data
2. Use normal browsing mode
3. Clear old data to free space
4. Disable extensions temporarily

Why aren't notifications working?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Check:**

1. Browser notification permissions (allow)
2. System notification settings (enabled)
3. GrowKitty Settings → Notifications (enabled)
4. Not in quiet hours
5. Sound not muted

Test with: Settings → Notifications → Send Test

See :doc:`troubleshooting#notification-issues` for more help.

My cat isn't animating. Why?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Possible Reasons:**

- Animations disabled in settings
- Auto-play turned off
- Performance/low power mode
- Browser limitation

**Solutions:**

1. Settings → Display → Animations → "Normal"
2. Settings → Cat → Auto-play → Enable
3. Reduce other tabs/applications
4. Try different browser

Features & Functionality
------------------------

Can I customize the app's appearance?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! Customization options:

- **Theme**: Light, Dark, Auto, Cozy, High Contrast
- **Color Scheme**: Blue, Green, Purple, Pink, Orange, Red
- **Font Size**: Small, Medium, Large, Extra Large
- **Animations**: None, Reduced, Normal, Enhanced
- **Custom CSS**: Advanced users can add custom styles

Settings → Display for all options.

Are there keyboard shortcuts?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currently, GrowKitty is primarily mouse/touch-driven. Keyboard navigation is limited to standard browser controls (Tab, Enter, etc.).

Keyboard shortcuts are planned for a future update!

Can I set multiple reminders for one habit?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Each habit can have one scheduled reminder. For multiple reminders:

- Create duplicate habits with different reminder times, or
- Use the "Repeat reminder" feature (every 30min, 1hr, 3hrs)

Is there a mobile app?
~~~~~~~~~~~~~~~~~~~~~~~

GrowKitty is a Progressive Web App (PWA). While not a native app, you can install it on your phone and it works just like one:

- Install from browser
- App icon on home screen
- Full-screen experience
- Works offline
- Push notifications

See: "How do I install GrowKitty?" above.

Can I share my progress with friends?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes:

1. Click Share button
2. Choose what to share:

   - Daily streak
   - Achievement unlock
   - Cat screenshot
   - Weekly progress

3. Select destination (social media, messaging, etc.)

Can I compete with friends?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, through leaderboards:

1. Settings → Privacy → Leaderboard Participation → Enable
2. Add friends by username
3. View Friends Leaderboard
4. Compare stats and cats

**Note:** You must enable visibility to appear on leaderboards.

Community & Support
-------------------

How do I report a bug?
~~~~~~~~~~~~~~~~~~~~~~

1. Go to `GitHub Issues <https://github.com/lillian-na/GrowKitty/issues>`_
2. Click "New Issue"
3. Select "Bug Report" template
4. Fill in details:

   - Description
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots
   - Environment (browser, OS)

5. Submit

How can I suggest a new feature?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Go to `GitHub Issues <https://github.com/lillian-na/GrowKitty/issues>`_
2. Click "New Issue"
3. Select "Feature Request" template
4. Describe your idea
5. Submit

Or discuss in GitHub Discussions first!

How can I contribute to GrowKitty?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We welcome all contributions:

- **Code**: Bug fixes, features, improvements
- **Documentation**: Improve guides, translations
- **Design**: UI/UX, cat designs, icons
- **Testing**: Report bugs, test features
- **Community**: Help others, spread the word

See :doc:`contributing` for detailed guidelines.

Where can I get help?
~~~~~~~~~~~~~~~~~~~~~~

**Resources:**

1. **Documentation**: You're reading it! See :doc:`index`
2. **Troubleshooting**: :doc:`troubleshooting` guide
3. **GitHub Issues**: Report bugs and ask questions
4. **GitHub Discussions**: Community help

**Contact:**

- GitHub: `@lillian-na <https://github.com/lillian-na>`_
- Email: [Contact via GitHub profile]

Is there a community?
~~~~~~~~~~~~~~~~~~~~~

Yes! Join us:

- **GitHub Discussions**: Talk with users and developers
- **GitHub Issues**: Participate in feature discussions
- **Social Media**: Share your progress (use #GrowKitty)

We'd love to see your cats and hear your success stories!

Advanced Questions
------------------

Can I modify the source code?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! GrowKitty is open-source under the MIT License. You can:

- View the source code
- Modify it for personal use
- Fork and create your own version
- Contribute improvements back

See :doc:`technical-overview` and :doc:`contributing`.

Can I self-host GrowKitty?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes:

1. Download source from GitHub
2. Upload to your web hosting
3. Access via your domain
4. No server-side code needed (static site)

Works with: GitHub Pages, Netlify, Vercel, or any static host.

Can I integrate GrowKitty with other apps?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currently, there's no official API. However, you can:

- Export/import data (JSON, CSV)
- Access LocalStorage programmatically
- Modify source code for custom integration

API development is on the roadmap!

How can I add custom missions?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**For Developers:**

1. Edit ``js/missions.js``
2. Add new mission template to ``missionTemplates`` array
3. Define title, requirements, and rewards
4. Test thoroughly

See :doc:`technical-overview` for architecture details.

Still Have Questions?
---------------------

If your question isn't answered here:

1. Check other documentation pages
2. Search `GitHub Issues <https://github.com/lillian-na/GrowKitty/issues>`_
3. Ask in `GitHub Discussions <https://github.com/lillian-na/GrowKitty/discussions>`_
4. Open a new issue

We're here to help! 🐱