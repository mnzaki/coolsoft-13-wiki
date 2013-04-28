**Aim:**
We wanted to develop a push service to get instant updates from the server.

Our implementation was inspired by this [article](http://jordanhollinger.com/2011/05/15/writing-an-ajax-long-polling-server-in-ruby-part-1) which was based mainly on whats called long polling.

**Long polling:**    
Basically the client sends a request to the server (with a huge timeout), then the server replies whenever the clients request is found. Unlike short polling where the client sends a request to the server every 2 or 3 seconds to check if anything changed.


**Implementation Idea:**    
The basic idea was to build a small app and have users use long polling to request any updates in the current page from this app. Then the app sends the users information to our main server which are stored in memory their so whenever an update related to those users is triggered the main server sends this update to our small app to update the users doing the long polling. We called our new app Coolster and the main app is Idearator.

**Building the app:**    
Coolster was built using [Thin](http://code.macournoyer.com/thin/) as a server and [sinatra](http://www.sinatrarb.com/) as a framework.