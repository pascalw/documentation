Frequently Asked Questions
==========================

Feature X was available in Miniflux 1?
--------------------------------------

Miniflux 2 doesn't try to reimplement all features of Miniflux 1.
The minimalist approach is pushed a little bit further.

If you really miss something, **you must contribute to the project**, but remember, **you have to keep the minimalist philosophy of Miniflux**.

Why are you not developing my feature request?
----------------------------------------------

- Developing a software takes a lot of time.
- This is a free and open source project, no one owes you anything.
- If you miss something, contribute to the project.
- Don't expect anyone to work for free.
- As mentioned above, the number of features is voluntarily limited. Nobody likes bloatware.
- Improving existing features is more important than adding new ones.

Why Miniflux stores favicons into the database?
-----------------------------------------------

Miniflux follows the `the Twelve Factors principle <https://12factor.net/>`_.
Nothing is stored on the local file system.
The application is designed to run on ephemeral containers without persistent storage.

How to create themes for Miniflux 2?
------------------------------------

As of now, Miniflux 2 doesn't have any mechanism to load external stylesheets to avoid dependencies.
Themes are embedded into the binary.

If you would like to submit a new official theme, you must send a pull-request.
But do not forget that **you will have to maintain your theme over the time**, otherwise, your theme will be removed from the code base.

Why there is no plugin system?
------------------------------

- Because this software has a minimalist approach.
- Because implementing a plugin system increase the complexity of the software.
- Because people do not maintain their plugins after a while.

What is "Save this article"?
----------------------------

"Save" sends the feed entry to third-party services like Pinboard or Instapaper if configured.

How are items removed from the database?
----------------------------------------

When a subscription is refreshed, entries marked as "removed" and not visible anymore in the XML feed are removed from the database.

What "Flush History" does?
--------------------------

"Flush History" changes the status of entries from "read" to "removed" (except for bookmarks).
Entries with the status "removed" are not visible in the user interface.

Is there any browser extensions for Miniflux?
---------------------------------------------

- Miniflux Notifications: `Chrome Web Store <https://chrome.google.com/webstore/detail/miniflux-notifications/jpeplhckmjlpahnkpblakfligkbfefkg>`_ - `Source Code <https://github.com/modInfo/miniflux-chrome-notifier>`_

Which binary do I need to use on my Raspberry Pi?
-------------------------------------------------

- Raspberry Pi A, A+, B, B+, Zero: :code:`miniflux-linux-armv6` compiled with :code:`GOARM=6`
- Raspberry Pi 2, 3: :code:`miniflux-linux-armv7` compiled with :code:`GOARM=7`

Why SQL migrations are not executed automatically?
--------------------------------------------------

- Because it's a source of problems.
- Only one process should manipulate the database schema at once.
- If you run multiple containers with an orchestrator that may cause issues.
- You can still run the migrations by defining the variable ``RUN_MIGRATIONS=1``.
