API Reference
=============

This document provides detailed reference for GrowKitty's JavaScript API, useful for developers who want to extend or integrate with the application.

Core API
--------

HabitManager
~~~~~~~~~~~~

Manages all habit-related operations.

**Methods**

``addHabit(config)``
^^^^^^^^^^^^^^^^^^^^

Creates a new habit.

**Parameters:**

.. code-block:: javascript

   {
     name: string,           // Required: Habit name
     category: string,       // Required: Category identifier
     frequency: string,      // 'daily', 'weekly', or 'custom'
     reminderTime: string,   // Optional: 'HH:MM' format
     notes: string          // Optional: Additional notes
   }

**Returns:** ``Habit`` object

**Example:**

.. code-block:: javascript

   const habit = HabitManager.addHabit({
     name: 'Morning Exercise',
     category: 'health',
     frequency: 'daily',
     reminderTime: '07:00'
   });

``getHabit(id)``
^^^^^^^^^^^^^^^^

Retrieves a habit by ID.

**Parameters:**

- ``id`` (string): Habit identifier

**Returns:** ``Habit`` object or ``null``

**Example:**

.. code-block:: javascript

   const habit = HabitManager.getHabit('habit_12345');

``updateHabit(id, updates)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Updates an existing habit.

**Parameters:**

- ``id`` (string): Habit identifier
- ``updates`` (object): Fields to update

**Returns:** Updated ``Habit`` object

**Example:**

.. code-block:: javascript

   HabitManager.updateHabit('habit_12345', {
     name: 'Evening Exercise',
     reminderTime: '18:00'
   });

``deleteHabit(id)``
^^^^^^^^^^^^^^^^^^^

Deletes a habit permanently.

**Parameters:**

- ``id`` (string): Habit identifier

**Returns:** ``boolean`` (success status)

**Example:**

.. code-block:: javascript

   const success = HabitManager.deleteHabit('habit_12345');

``completeHabit(id, date)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Marks a habit as completed.

**Parameters:**

- ``id`` (string): Habit identifier
- ``date`` (Date, optional): Completion date (defaults to today)

**Returns:** ``Completion`` object

**Example:**

.. code-block:: javascript

   const completion = HabitManager.completeHabit('habit_12345');
   
   // Or for a specific date
   const pastCompletion = HabitManager.completeHabit(
     'habit_12345', 
     new Date('2025-01-15')
   );

``skipHabit(id, reason)``
^^^^^^^^^^^^^^^^^^^^^^^^^

Skips a habit with an optional reason.

**Parameters:**

- ``id`` (string): Habit identifier
- ``reason`` (string, optional): Skip reason

**Returns:** ``Skip`` object

**Example:**

.. code-block:: javascript

   HabitManager.skipHabit('habit_12345', 'Feeling unwell');

``getHabits(filter)``
^^^^^^^^^^^^^^^^^^^^^

Retrieves habits with optional filtering.

**Parameters:**

.. code-block:: javascript

   {
     category: string,      // Optional: Filter by category
     frequency: string,     // Optional: Filter by frequency
     active: boolean       // Optional: Only active habits
   }

**Returns:** Array of ``Habit`` objects

**Example:**

.. code-block:: javascript

   // Get all daily health habits
   const habits = HabitManager.getHabits({
     category: 'health',
     frequency: 'daily',
     active: true
   });

``getHabitStats(id, days)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Calculates statistics for a habit.

**Parameters:**

- ``id`` (string): Habit identifier
- ``days`` (number, optional): Number of days to analyze (default: 30)

**Returns:** Statistics object

.. code-block:: javascript

   {
     successRate: number,     // 0-100 percentage
     currentStreak: number,   // Days in a row
     longestStreak: number,   // Best streak ever
     totalCompletions: number,
     averagePerWeek: number,
     lastCompleted: Date
   }

**Example:**

.. code-block:: javascript

   const stats = HabitManager.getHabitStats('habit_12345', 90);
   console.log(`Success rate: ${stats.successRate}%`);

MissionSystem
~~~~~~~~~~~~~

Manages missions and challenges.

**Methods**

``getDailyMissions()``
^^^^^^^^^^^^^^^^^^^^^^

Retrieves today's missions.

**Returns:** Array of ``Mission`` objects

**Example:**

.. code-block:: javascript

   const missions = MissionSystem.getDailyMissions();
   missions.forEach(mission => {
     console.log(mission.title, mission.progress);
   });

``checkMissionProgress(missionId)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Updates and returns mission progress.

**Parameters:**

- ``missionId`` (string): Mission identifier

**Returns:** ``Mission`` object with updated progress

**Example:**

.. code-block:: javascript

   const mission = MissionSystem.checkMissionProgress('mission_123');
   if (mission.progress >= 1.0) {
     console.log('Mission completed!');
   }

``completeMission(missionId)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Manually completes a mission and grants rewards.

**Parameters:**

- ``missionId`` (string): Mission identifier

**Returns:** ``Reward`` object

**Example:**

.. code-block:: javascript

   const reward = MissionSystem.completeMission('mission_123');
   console.log(`Earned ${reward.xp} XP and ${reward.coins} coins`);

``refreshMissions()``
^^^^^^^^^^^^^^^^^^^^^

Generates new random missions.

**Returns:** Array of new ``Mission`` objects

**Example:**

.. code-block:: javascript

   // Costs 75 coins
   const newMissions = MissionSystem.refreshMissions();

CatController
~~~~~~~~~~~~~

Controls the virtual cat's behavior and appearance.

**Methods**

``getCat()``
^^^^^^^^^^^^

Retrieves current cat state.

**Returns:** ``Cat`` object

.. code-block:: javascript

   {
     name: string,
     stage: string,         // 'kitten', 'young', 'adult', 'master', 'legendary'
     level: number,
     mood: string,          // 'happy', 'content', 'neutral', 'sad', 'sick'
     happiness: number,     // 0-100
     accessories: Array
   }

**Example:**

.. code-block:: javascript

   const cat = CatController.getCat();
   console.log(`${cat.name} is ${cat.mood}`);

``updateCatName(name)``
^^^^^^^^^^^^^^^^^^^^^^^

Changes the cat's name.

**Parameters:**

- ``name`` (string): New name (max 20 characters)

**Returns:** Updated ``Cat`` object

**Example:**

.. code-block:: javascript

   CatController.updateCatName('Whiskers');

``feedCat(item)``
^^^^^^^^^^^^^^^^^

Gives food to the cat.

**Parameters:**

- ``item`` (object): Food item

**Returns:** Reaction object

**Example:**

.. code-block:: javascript

   const reaction = CatController.feedCat({
     type: 'treat',
     effect: 'happiness_boost'
   });

``petCat()``
^^^^^^^^^^^^

Interacts with the cat through petting.

**Returns:** Reaction object

**Example:**

.. code-block:: javascript

   const reaction = CatController.petCat();
   // Cat shows happiness animation

``equipAccessory(itemId, slot)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Equips an accessory on the cat.

**Parameters:**

- ``itemId`` (string): Item identifier
- ``slot`` (string): 'hat', 'clothes', or 'accessory'

**Returns:** ``boolean`` (success status)

**Example:**

.. code-block:: javascript

   const success = CatController.equipAccessory('item_hat_01', 'hat');

``unequipAccessory(slot)``
^^^^^^^^^^^^^^^^^^^^^^^^^^

Removes an equipped accessory.

**Parameters:**

- ``slot`` (string): Slot to clear

**Returns:** ``boolean`` (success status)

**Example:**

.. code-block:: javascript

   CatController.unequipAccessory('hat');

RewardSystem
~~~~~~~~~~~~

Handles all reward calculations and distributions.

**Methods**

``calculateReward(action, multiplier)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Calculates reward amount for an action.

**Parameters:**

- ``action`` (string): Action type ('habitComplete', 'missionComplete', etc.)
- ``multiplier`` (number, optional): Reward multiplier (default: 1.0)

**Returns:** Reward object

.. code-block:: javascript

   {
     xp: number,
     coins: number,
     gems: number
   }

**Example:**

.. code-block:: javascript

   const reward = RewardSystem.calculateReward('habitComplete', 1.5);

``grantReward(reward, source)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Grants rewards to the user.

**Parameters:**

- ``reward`` (object): Reward amounts
- ``source`` (string): Source description

**Returns:** Updated user object

**Example:**

.. code-block:: javascript

   RewardSystem.grantReward({
     xp: 100,
     coins: 20,
     gems: 0
   }, 'Daily mission completion');

``purchase(itemId, cost)``
^^^^^^^^^^^^^^^^^^^^^^^^^^

Processes a shop purchase.

**Parameters:**

- ``itemId`` (string): Item to purchase
- ``cost`` (object): Cost in currencies

**Returns:** Purchase result object

**Example:**

.. code-block:: javascript

   const result = RewardSystem.purchase('hat_01', {
     coins: 50,
     gems: 0
   });
   
   if (result.success) {
     console.log('Purchase successful!');
   }

Storage API
-----------

StorageManager
~~~~~~~~~~~~~~

Handles data persistence.

**Methods**

``save(data)``
^^^^^^^^^^^^^^

Saves application state to LocalStorage.

**Parameters:**

- ``data`` (object): Application state

**Returns:** ``boolean`` (success status)

**Example:**

.. code-block:: javascript

   const success = StorageManager.save({
     user: userData,
     habits: habitsData,
     cat: catData
   });

``load()``
^^^^^^^^^^

Loads application state from LocalStorage.

**Returns:** Application state object

**Example:**

.. code-block:: javascript

   const state = StorageManager.load();

``export(format)``
^^^^^^^^^^^^^^^^^^

Exports data in specified format.

**Parameters:**

- ``format`` (string): 'json' or 'csv'

**Returns:** Serialized data string

**Example:**

.. code-block:: javascript

   const json = StorageManager.export('json');
   const csv = StorageManager.export('csv');

``import(data, format)``
^^^^^^^^^^^^^^^^^^^^^^^^

Imports data from serialized format.

**Parameters:**

- ``data`` (string): Serialized data
- ``format`` (string): 'json' or 'csv'

**Returns:** ``boolean`` (success status)

**Example:**

.. code-block:: javascript

   const jsonData = '{"user": {...}, "habits": [...]}';
   const success = StorageManager.import(jsonData, 'json');

``clear()``
^^^^^^^^^^^

Clears all stored data.

**Returns:** ``boolean`` (success status)

**Example:**

.. code-block:: javascript

   if (confirm('Delete all data?')) {
     StorageManager.clear();
   }

Event System
------------

EventBus
~~~~~~~~

Central event management.

**Methods**

``on(event, callback)``
^^^^^^^^^^^^^^^^^^^^^^^

Registers an event listener.

**Parameters:**

- ``event`` (string): Event name
- ``callback`` (function): Handler function

**Example:**

.. code-block:: javascript

   EventBus.on('habit:completed', (habit) => {
     console.log(`Completed: ${habit.name}`);
     showNotification('Great job!');
   });

``off(event, callback)``
^^^^^^^^^^^^^^^^^^^^^^^^

Removes an event listener.

**Parameters:**

- ``event`` (string): Event name
- ``callback`` (function): Handler function to remove

**Example:**

.. code-block:: javascript

   const handler = (habit) => { /* ... */ };
   EventBus.on('habit:completed', handler);
   
   // Later...
   EventBus.off('habit:completed', handler);

``emit(event, data)``
^^^^^^^^^^^^^^^^^^^^^

Triggers an event.

**Parameters:**

- ``event`` (string): Event name
- ``data`` (any): Event data

**Example:**

.. code-block:: javascript

   EventBus.emit('habit:completed', {
     id: 'habit_123',
     name: 'Morning Exercise',
     timestamp: Date.now()
   });

Standard Events
~~~~~~~~~~~~~~~

Application events you can listen to:

**Habit Events**

- ``habit:added`` - New habit created
- ``habit:updated`` - Habit modified
- ``habit:deleted`` - Habit removed
- ``habit:completed`` - Habit marked complete
- ``habit:skipped`` - Habit skipped

**Mission Events**

- ``mission:generated`` - New missions created
- ``mission:progress`` - Mission progress updated
- ``mission:completed`` - Mission finished

**Cat Events**

- ``cat:fed`` - Cat was fed
- ``cat:petted`` - Cat was petted
- ``cat:mood_changed`` - Cat mood updated
- ``cat:leveled_up`` - Cat reached new stage
- ``cat:accessory_equipped`` - Accessory added

**User Events**

- ``user:leveled_up`` - User gained a level
- ``user:reward_earned`` - Reward granted
- ``user:purchase_made`` - Shop purchase completed

**System Events**

- ``app:loaded`` - Application initialized
- ``app:saved`` - Data saved to storage
- ``app:error`` - Error occurred

Example Usage
^^^^^^^^^^^^^

.. code-block:: javascript

   // Listen for multiple events
   EventBus.on('habit:completed', (habit) => {
     CatController.react('celebrate');
     showNotification(`Completed: ${habit.name}`);
   });
   
   EventBus.on('user:leveled_up', (data) => {
     showLevelUpModal(data.level);
     playSound('levelup');
   });
   
   EventBus.on('app:error', (error) => {
     console.error('Application error:', error);
     showErrorNotification(error.message);
   });

Utility Functions
-----------------

DateUtils
~~~~~~~~~

Date manipulation utilities.

``isToday(date)``
^^^^^^^^^^^^^^^^^

Checks if date is today.

**Parameters:**

- ``date`` (Date): Date to check

**Returns:** ``boolean``

``isSameDay(date1, date2)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Checks if two dates are the same day.

**Parameters:**

- ``date1`` (Date): First date
- ``date2`` (Date): Second date

**Returns:** ``boolean``

``getStartOfDay(date)``
^^^^^^^^^^^^^^^^^^^^^^^

Gets start of day (00:00:00).

**Parameters:**

- ``date`` (Date): Input date

**Returns:** ``Date``

``getDaysDifference(date1, date2)``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Calculates days between dates.

**Parameters:**

- ``date1`` (Date): Start date
- ``date2`` (Date): End date

**Returns:** ``number``

StringUtils
~~~~~~~~~~~

String manipulation utilities.

``sanitize(str)``
^^^^^^^^^^^^^^^^^

Sanitizes HTML in strings.

**Parameters:**

- ``str`` (string): Input string

**Returns:** Sanitized string

``truncate(str, length)``
^^^^^^^^^^^^^^^^^^^^^^^^^

Truncates string to length.

**Parameters:**

- ``str`` (string): Input string
- ``length`` (number): Max length

**Returns:** Truncated string

``generateId()``
^^^^^^^^^^^^^^^^

Generates unique identifier.

**Returns:** Unique string ID

Example Integration
-------------------

Complete Example
~~~~~~~~~~~~~~~~

.. code-block:: javascript

   // Initialize the application
   document.addEventListener('DOMContentLoaded', () => {
     // Load saved data
     const state = StorageManager.load();
     
     // Set up event listeners
     EventBus.on('habit:completed', (habit) => {
       // Update cat mood
       const successRate = HabitManager.getSuccessRate();
       CatController.updateMood(successRate);
       
       // Grant rewards
       const reward = RewardSystem.calculateReward('habitComplete');
       RewardSystem.grantReward(reward, 'Habit completion');
       
       // Check mission progress
       const missions = MissionSystem.getDailyMissions();
       missions.forEach(mission => {
         MissionSystem.checkMissionProgress(mission.id);
       });
       
       // Save state
       StorageManager.save(AppState);
     });
     
     // Render UI
     renderDashboard();
   });

Next Steps
----------

For more detailed examples and use cases:

- :doc:`technical-overview` - Architecture and design patterns
- :doc:`contributing` - Contribution guidelines
- `GitHub Repository <https://github.com/lillian-na/GrowKitty>`_ - Source code