**Aim:**
We wanted to develop a push service to get instant updates from the server.

Our implementation was inspired by this [article](http://jordanhollinger.com/2011/05/15/writing-an-ajax-long-polling-server-in-ruby-part-1). The article's approach was to do the following:  
1. Build a small app.  
2. Have users use long polling for requesting updates from this new app.  
3. The small app requests the updates from the main server using short polling.    

**Short polling:**    
The client sends a request to the server every 2 or 3 seconds to check if anything has changed.

**Long polling:**    
Unlike short polling, the client sends a request to the server once (with a huge timeout), then the server replies whenever the clients request is found.


**Implementation Idea:**    
The basic idea was to build a small app and have users use long polling to request any updates in the current page from this app. Then the app sends the users information to our main server which are stored in memory their so whenever an update related to those users is triggered the main server sends this update to our small app to update the users doing the long polling. We called our new app Coolster and the main app is Idearator.

The difference between our implementation and the one in the article is how getting updates from the main server is handled. We won't be using short polling to get updates from the main server instead the server sends a request to the small app whenever a change occurs. 

**Building the app:**    
Coolster was built using [Thin](http://code.macournoyer.com/thin/) as a server and [sinatra](http://www.sinatrarb.com/) as a framework.

**Resources:**  
1. [ Jordan Hollinger's article](http://jordanhollinger.com/2011/05/15/writing-an-ajax-long-polling-server-in-ruby-part-1).