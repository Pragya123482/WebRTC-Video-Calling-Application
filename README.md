# WebRTC-Video-Calling-Application
This would build a set up of a bare bones browser-to-browser video calling app

Features
========
- PSTN Calling
 - Make calls using WebRTC
- Web/app calling 
 - Make and receive calls using WebRTC
 - Call both web clients and native (iOS and Android)
- SIP calling
 - Make calls connected to SIP clients
- Conference calling
- Instant messaging
 - Cross platform, using native SDK's for iOS and Android
 - Conversations with up to 10 participants
 - Delivery receipts
- Video calling (beta)
 - Web clients only
- Group p2p calling
 - Web clients only
- Phone number verification 
  - SMS verification
  - Callout verification
- Partner user management
 - Authentication ticket for session creation
 - Allows full user management for partner
 - Sample python (tornado) backend in samples folder (SinchAUTHsample)
 - NOTE: Review your app setting for "JS Auth" in the Sinch portal
- Sinch user management
 - Create user, update password and basic profile
 - Authenticate as user
 - Generate authentication tickets when running as backend
 
 Should you encounter any bugs, glitches, lack of functionality or other problems
using our SDK, please send us an email to rishijha.pragya@gmail.com 
Your help in this regard is greatly appreciated.

Getting Started
===============
Familiarise yourself with the user guide (documentation folder or online).

Have a look at the Sample App in the samples/ folder, where you'll find:
-IMsample, our Instant Messaging sample app
- PSTNsample, our PSTN calling sample app
- WEBsample, our Web to Web calling sample app
- AUTHsample, our sample for demonstrating integrating a custom backend
  for user authentication (useful for native app compatability)
- python-backend-sample, a sample backend for Sinch written in Python 
  (see README.md for more information on getting started)
- VIDEOsample, sample for person to person video calling
- GROUPVIDEOsample, sample for group video conferencing
- VERsample, sample for SMS number verification
- CALLOUTsample, sample for Callout number verification

These sample apps demonstrate user management, session handling and more. 
The interesting stuff can be found in the .js files.

In order to get started follow these steps: 

1. Try open http://localhost/Video%20Call/samples/VIDEOsample/index.html in two web-browser tabs. (Chrome or Firefox). 
   Open the developer console. 
2. In the browser window you should see a web form where you can either create 
   a new user or login as a user. 
3. Try creating a user
4.Login on the first tab with userA and on the second tab with userB.
From the first tab, place a call to userB and pick up the call.

Have a look at the source code in IMsample.js, enable the onLogMessage callback 
if you're curious about the activity under the hood. It's a good way to have 
logging enabled during development for easy error tracking.

You can also activate session loading by enabling the if-statement on line 45, 
by removing "false" from the if-statement. The PSTN and AUTH sample application 
has this activated by default, please see the PSTNsample.js file for reference.

As for the PSTN sample app, you may have to load the application from a web 
server (can be local), depending on the security settings for WebRTC in your 
browser.  

Known issues
============
- There is an issue running too many instances at the same time. No more than 
  5-6 instances can be run at the same time in the same browser. 
  (if problem experienced, restart browser and only run one instance and try 
  again with fewer instances)
- After three failed login attempts on one user accounts, that account is 
  locked for a while with no ability to unlock (when using Sinch auth).
- Restore messages missed since last login is currently disabled. 
- When browser close, any ongoing PSTN calls are not terminated properly but 
  relies on B-side doing a time-out. (~ 1 minute)
- Browserify is not yet supported for Node JS distribution. 
