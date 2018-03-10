Project D.A.D.D.A.
==================

A Distributed Automatic Dalmatian Detection Agent.

This will use a Keras based neural network to detect Dalmatians in events detected by ZoneMinder.

This allows one to run events on a ZoneMinder server by dadda to check if they contain a Dalmatian.

This could be used for any other pet or other object monitoring scenario, but was specifically written for detecting Dalmatians. None of the code specifically expects there to actually _be_ a Dalmatian, however all the defaults do.

Processes
---------

**The detection process will be to:**

1. Connect to a nominated ZoneMinder server
2. Finding all events after a specified date that match a specified criteria which do not contain the phrase "Dalmatian Detected" in their notes.
3. For each event, if any frame has more than a nominated threshold of Dalmatian activity, it's notes will be updated to have "Dalmatian Detected" as an extra line

It's expected that this will be run as an automated service every so often (or on-demand after every event is completed if that's possible)

This can be used to categories events which are "not interesting" and are retained for less time.

**Learning will be done by:**

1. Manually adding or removing the phrase "Dalmatian Detected" on events in ZoneMinder based on the presence of a Dalmatian in the event's footage (*NOTE* this does not help us with detecting which _exact frames_ contain a Dalmatian, so if it runs through the view of a camera, we'll assume that all frames, even the ones without Dalmatian activity contain a Dalmatian.)
2. The learning script will connect to the ZoneMinder server and pull all events matching a specified criteria (including a date range)
3. The neural network will be trained on all frames in the event with a score above a set threshold.

Installation
------------

It's recommend that you use this with a virtualenv of some sort.

1. Install Keras and a supported neural network of your choice. It's recommended that you install GPU acceleration if you're planning to do any learning.
2. Run `command` to install any remaining dependencies

Known Bugs
----------

None yet =)

Hacking
-------

No idea yet, I'm very new to this =)
