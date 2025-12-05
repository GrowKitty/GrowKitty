Troubleshooting
===============

This guide helps you diagnose and resolve common issues with GrowKitty.

Quick Diagnostics
-----------------

Run Basic Checks
~~~~~~~~~~~~~~~~

Before diving into specific issues:

1. **Clear browser cache** (Ctrl+Shift+Del / Cmd+Shift+Del)
2. **Try incognito/private mode**
3. **Check browser console** (F12) for errors
4. **Verify browser version** is supported
5. **Test on different device** if available

Common Issues
-------------

Installation & Loading
~~~~~~~~~~~~~~~~~~~~~~

**Issue: Blank Page After Opening**

**Symptoms:**

- White/blank screen
- No content displays
- Page loads but nothing appears

**Solutions:**

.. code-block:: text

   1. Check browser console (F12) for JavaScript errors
   2. Verify all files were extracted correctly
   3. Ensure index.html is in the root directory
   4. Try using a local server instead of file://
   5. Disable browser extensions temporarily

**Step-by-step fix:**

.. code-block:: bash

   # Start a local server
   python -m http.server 8000
   
   # Or with Node.js
   npx http-server -p 8000

**Issue: Images Not Loading**

**Symptoms:**

- Broken image icons
- Missing cat graphics
- UI icons don't appear

**Solutions:**

1. Check file paths in console (F12)
2. Verify ``assets/`` folder exists
3. Confirm image files are present
4. Check file extensions match code (.png, .svg, etc.)

**File structure check:**

.. code-block:: text

   GrowKitty/
   ├── index.html
   ├── assets/
   │   ├── images/
   │   │   ├── cat-kitten.png
   │   │   ├── cat-young.png
   │   │   └── ...
   │   └── icons/
   │       ├── habit-icon.svg
   │       └── ...

**Issue: CSS Not Applied**

**Symptoms:**

- Unstyled page
- Plain HTML layout
- Missing colors/fonts

**Solutions:**

1. Check ``css/style.css`` exists
2. Verify link tags in ``index.html``
3. Clear browser cache
4. Check console for CSS load errors

Data & Storage
~~~~~~~~~~~~~~

**Issue: Data Not Saving**

**Symptoms:**

- Changes disappear after refresh
- Habits not persisting
- Settings reset

**Solutions:**

1. **Check LocalStorage permissions:**

   - Browser Settings → Privacy
   - Allow site data and cookies
   - Whitelist localhost if needed

2. **Verify storage quota:**

   .. code-block:: javascript

      // Check in browser console
      navigator.storage.estimate().then(estimate => {
        console.log(`Used: ${estimate.usage} bytes`);
        console.log(`Quota: ${estimate.quota} bytes`);
      });

3. **Manual save:**

   - Open browser console (F12)
   - Run: ``StorageManager.save(AppState)``

**Issue: Data Corruption**

**Symptoms:**

- App crashes on load
- Strange behavior
- Missing data fields

**Solutions:**

1. **Export backup first (if possible):**

   .. code-block:: javascript

      // In console
      const backup = localStorage.getItem('growkitty_data');
      console.log(backup); // Copy this

2. **Clear corrupted data:**

   - Settings → Data Management → Clear All Data
   - Or manually: ``localStorage.clear()``

3. **Import clean backup** if available

**Issue: Unable to Export Data**

**Symptoms:**

- Export button doesn't work
- Downloaded file is empty
- Error during export

**Solutions:**

.. code-block:: javascript

   // Manual export via console
   const data = StorageManager.load();
   const json = JSON.stringify(data, null, 2);
   
   // Copy and save to file
   console.log(json);
   
   // Or trigger download
   const blob = new Blob([json], { type: 'application/json' });
   const url = URL.createObjectURL(blob);
   const a = document.createElement('a');
   a.href = url;
   a.download = 'growkitty-backup.json';
   a.click();

Functionality Issues
~~~~~~~~~~~~~~~~~~~~

**Issue: Habits Not Completing**

**Symptoms:**

- Checkbox doesn't work
- No response when clicking
- Completion doesn't register

**Solutions:**

1. Check browser console for errors
2. Verify habit ID exists
3. Test in different browser
4. Clear cache and reload

**Manual completion:**

.. code-block:: javascript

   // In console, find habit ID from habit list
   const habitId = 'habit_12345';
   HabitManager.completeHabit(habitId);

**Issue: Missions Not Updating**

**Symptoms:**

- Progress stays at 0%
- Missions don't complete
- New missions don't generate

**Solutions:**

1. **Refresh missions manually:**

   .. code-block:: javascript

      // In console
      MissionSystem.refreshMissions();

2. **Check mission requirements:**

   - Ensure you meet the criteria
   - Verify habits in correct category
   - Check time constraints

3. **Reset mission system:**

   - Settings → Advanced → Reset Missions

**Issue: Cat Not Responding**

**Symptoms:**

- Cat doesn't animate
- No mood changes
- Static image only

**Solutions:**

1. **Check animation settings:**

   - Settings → Display → Animations (should not be "None")
   - Settings → Cat → Auto-play Animations (enable)

2. **Verify cat data:**

   .. code-block:: javascript

      // In console
      const cat = CatController.getCat();
      console.log(cat);

3. **Reset cat:**

   - Settings → Cat → Reset to Default

4. **Check performance:**

   - Close other tabs/applications
   - Reduce animation speed if lag

Performance Issues
~~~~~~~~~~~~~~~~~~

**Issue: App Running Slowly**

**Symptoms:**

- Laggy animations
- Slow page load
- Delayed interactions

**Solutions:**

**Immediate fixes:**

1. Close unused browser tabs
2. Settings → Display → Animations → "Reduced"
3. Settings → Cat → Animation Speed → "Fast"
4. Disable auto-play animations

**Long-term optimizations:**

1. **Clean up old data:**

   .. code-block:: javascript

      // Remove completions older than 1 year
      HabitManager.cleanupOldData(365);

2. **Reduce mission count:**

   - Settings → Missions → Daily Mission Count → 2

3. **Use lighter theme:**

   - Settings → Display → Theme → "Light Mode"

**Issue: High Memory Usage**

**Symptoms:**

- Browser becomes unresponsive
- System slowdown
- Crash or freeze

**Solutions:**

1. **Monitor storage:**

   - Settings → Data Management → Storage Usage

2. **Export and clear data:**

   - Export important data first
   - Clear all data
   - Import only recent data

3. **Browser-specific:**

   - Chrome: chrome://settings/clearBrowserData
   - Firefox: about:preferences#privacy

Notification Issues
~~~~~~~~~~~~~~~~~~~

**Issue: Reminders Not Working**

**Symptoms:**

- No notifications appear
- Reminders don't fire
- Silent notifications

**Solutions:**

1. **Check permissions:**

   **Chrome:**
   
   - Click lock icon in address bar
   - Notifications → Allow

   **Firefox:**
   
   - Click shield icon
   - Permissions → Notifications → Allow

2. **Verify notification settings:**

   - Settings → Notifications → Habit Reminders (enable)
   - Check quiet hours aren't active
   - Verify sound is not "None"

3. **Test notification:**

   .. code-block:: javascript

      // In console
      new Notification('Test', {
        body: 'If you see this, notifications work!',
        icon: 'assets/icons/app-icon.png'
      });

4. **System notifications:**

   - **Windows:** Settings → System → Notifications
   - **Mac:** System Preferences → Notifications
   - **Linux:** Depends on desktop environment

**Issue: Too Many Notifications**

**Solutions:**

1. Disable non-essential notifications
2. Enable quiet hours
3. Reduce reminder frequency
4. Use "Single notification" mode

Mobile Issues
~~~~~~~~~~~~~

**Issue: Not Responsive on Mobile**

**Symptoms:**

- Tiny text
- Elements overflow screen
- Buttons hard to tap

**Solutions:**

1. **Check viewport meta tag** in index.html:

   .. code-block:: html

      <meta name="viewport" 
            content="width=device-width, initial-scale=1.0">

2. **Use mobile-optimized settings:**

   - Increase font size
   - Enable touch gestures
   - Simplify animations

3. **Install as PWA:**

   - Browser menu → "Add to Home Screen"
   - Better mobile experience

**Issue: Offline Mode Not Working**

**Symptoms:**

- Requires internet connection
- Data doesn't load offline
- Features unavailable

**Solutions:**

1. **Enable Service Worker** (if implemented)
2. **Check cache storage:**

   - Browser console: ``caches.keys()``

3. **Preload critical assets**
4. **Use airplane mode** to test

Browser-Specific Issues
------------------------

Chrome Issues
~~~~~~~~~~~~~

**LocalStorage Disabled**

.. code-block:: text

   Chrome Settings → Privacy and Security
   → Cookies and other site data
   → Allow all cookies

**Autoplay Policy Blocks Sounds**

.. code-block:: text

   Chrome Settings → Privacy and Security
   → Site Settings → Sound
   → Add growkitty.app to Allowed

Firefox Issues
~~~~~~~~~~~~~~

**Tracking Protection**

.. code-block:: text

   Shield icon in address bar
   → Turn off Enhanced Tracking Protection

**Strict Privacy Settings**

.. code-block:: text

   about:preferences#privacy
   → Standard protection

Safari Issues
~~~~~~~~~~~~~

**Prevent Cross-Site Tracking**

.. code-block:: text

   Safari → Preferences → Privacy
   → Uncheck "Prevent cross-site tracking"

**LocalStorage in Private Mode**

- Private browsing doesn't persist data
- Use regular browsing mode

Edge Issues
~~~~~~~~~~~

**Similar to Chrome** (Chromium-based)

- Follow Chrome solutions
- Additional: Edge Settings → Privacy

Error Messages
--------------

Common Error Messages and Fixes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**"QuotaExceededError"**

- **Cause:** LocalStorage full (usually 5-10MB limit)
- **Fix:** Export data, clear storage, import essentials

**"SecurityError: Failed to read 'localStorage'"**

- **Cause:** Browser privacy settings
- **Fix:** Allow cookies and site data

**"TypeError: Cannot read property of undefined"**

- **Cause:** Data corruption or missing field
- **Fix:** Clear data and restart

**"NetworkError when attempting to fetch resource"**

- **Cause:** File not found or wrong path
- **Fix:** Verify file structure, use absolute paths

**"Uncaught ReferenceError: X is not defined"**

- **Cause:** JavaScript file not loaded
- **Fix:** Check script tags in index.html, verify file paths

Debug Mode
----------

Enable Debug Mode
~~~~~~~~~~~~~~~~~

1. Settings → Advanced → Developer Options
2. Enable "Debug Mode"
3. Open browser console (F12)

Debug Information
~~~~~~~~~~~~~~~~~

Useful diagnostic data:

.. code-block:: javascript

   // Get full app state
   console.log(AppState);
   
   // Check storage
   console.log(localStorage.getItem('growkitty_data'));
   
   // Verify event listeners
   console.log(EventBus.events);
   
   // Test habit functions
   console.log(HabitManager.getHabits());
   
   // Cat status
   console.log(CatController.getCat());
   
   // Recent errors
   console.log(ErrorLog.getRecent());

Export Debug Report
~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

   // Generate comprehensive debug report
   const report = {
     timestamp: new Date(),
     browser: navigator.userAgent,
     viewport: {
       width: window.innerWidth,
       height: window.innerHeight
     },
     storage: {
       used: localStorage.length,
       size: new Blob([localStorage.getItem('growkitty_data')]).size
     },
     state: AppState,
     errors: ErrorLog.getRecent(50),
     performance: performance.getEntries()
   };
   
   console.log(JSON.stringify(report, null, 2));

Getting Help
------------

Self-Help Resources
~~~~~~~~~~~~~~~~~~~

1. Check :doc:`faq` for quick answers
2. Review :doc:`usage` guide
3. Search `GitHub Issues <https://github.com/lillian-na/GrowKitty/issues>`_
4. Read through this troubleshooting guide again

Reporting Bugs
~~~~~~~~~~~~~~

If issue persists, report it:

**Information to Include:**

1. **Environment:**

   - Browser name and version
   - Operating system
   - Device type (desktop/mobile)

2. **Steps to Reproduce:**

   - What were you trying to do?
   - What did you click/type?
   - Sequence of actions

3. **Expected vs Actual:**

   - What should have happened?
   - What actually happened?

4. **Screenshots/Videos:**

   - Visual proof helpful
   - Include console errors

5. **Debug Report:**

   - Export from Debug Mode
   - Attach to issue

**Where to Report:**

- `GitHub Issues <https://github.com/lillian-na/GrowKitty/issues>`_
- Use issue template
- Tag appropriately (bug, enhancement, etc.)

Emergency Recovery
------------------

Complete Reset
~~~~~~~~~~~~~~

Last resort if nothing else works:

**1. Backup Everything Possible**

.. code-block:: javascript

   // Copy this from console
   const backup = localStorage.getItem('growkitty_data');
   console.log(backup);

**2. Clear All Data**

.. code-block:: javascript

   // Nuclear option - deletes everything
   localStorage.clear();
   sessionStorage.clear();
   
   // Clear cache
   caches.keys().then(keys => {
     keys.forEach(key => caches.delete(key));
   });

**3. Hard Refresh**

- **Windows/Linux:** Ctrl + Shift + R
- **Mac:** Cmd + Shift + R

**4. Reinstall**

- Delete local files
- Re-download from GitHub
- Extract fresh copy
- Start clean

Recovery from Backup
~~~~~~~~~~~~~~~~~~~~

If you have a backup file:

1. Settings → Data Management
2. Import Data
3. Select backup file
4. Choose "Replace all data"
5. Confirm import
6. Refresh page

Preventive Measures
-------------------

Avoid Future Issues
~~~~~~~~~~~~~~~~~~~

**Regular Maintenance:**

1. Export data weekly
2. Clear old completions monthly
3. Update browser regularly
4. Monitor storage usage
5. Keep backups

**Good Practices:**

1. Don't modify LocalStorage directly
2. Use export/import for transfers
3. Test changes in incognito first
4. Keep habit list manageable
5. Review settings periodically

**Performance Tips:**

1. Limit concurrent apps/tabs
2. Close unused browser windows
3. Restart browser weekly
4. Clear cache monthly
5. Update to latest version

Next Steps
----------

- :doc:`faq` - Quick answers to common questions
- :doc:`configuration` - Optimize your setup
- `GitHub Issues <https://github.com/lillian-na/GrowKitty/issues>`_ - Community support
