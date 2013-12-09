hookup
======

Overview
===
Android App to Hookup with people nearby and having same interests to connect.
So the rules are that people who will download and install this app, will have to fill one form about their interests and click "Search".

The app runs in background and after every 3-4 minutes, they sweep their nearby area, say 10-20 metres.

While sweeping, if the google maps api finds some other phones with this app installed in it, it will ask those other devices to pass it that table which contains all those interests.

When our app receives the other phone's interests, it will run a best match algorithm to check if the other person is a compatible match for this person. E.g. First person is female and likes men, dancing, action movies, etc. The other person is a men who likes women, movies, food, etc.

So, if the best match returns a good match, they both will be notified in their devices that there is a person with same interests within 10 METER Radius that you can HOOKUP with.
        They both will be given a chat window to chat and share their locations and personal information.
        
        
Implementation Points
===
1.  The app does not requires any sign-in or sign-out. It just needs to set a database in the client's device that contains his interests.
2.  The app does not needs any personal information to store. The only way use can share their personal information is by explicitly telling to the other person in the chat window.
3.  The first time the user runs the app, the app will store a random number in the client's device and store that random number in the database also. Upon each run the app will search for this random no. If it CAN find the random number, then it means that this is NOT the first run and hence they will directly will be taken to the control page where they can start the search.
    However, if the random number CANNOT be found, it means that the app is running for the first time, and it will ask users about their interests and upon pressing OK, it will start the search.
4.  The interests are editable by the way i.e. the users can edit their interests and re-start the search anytime they want.
5.  If the app finds more than 1 person, say 5 person, out of which 3 are fitting the best match, the chat window will create tabs, just like facebook messenger, to chat will all of them. The user can close any of the tab if they don;t like it.
6.  The settings page will contain option to "Stop" the search, "To go back and change their interests", and to re-start their search.
7.  If the user closes the app, the "Search nearby devices" would still be working in the background. This process can only be stopped either by pressing the "Stop" button in the settings page, or by killing this process in the android process window.
8.  In the app, we can also build an option to "Set their profile pictures and share their names". This way, the two persons can easily (re)indentify each other.
9.  A module can also be built to store friends. So when some of those friends are nearby, they also can be alerted. This module can be turned off/on. To implement this, we only need to store the "device unique ID" in the database. So now in each sweep, it also searches for these devices. And if any one or more of them are present, everyone will be notified.
