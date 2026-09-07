## MS Frog Generator 2 (picoCTF, Web Exploitation, Hard)

As of today, this has definitely been the most difficult cybersecurity challenge I have done so far. For this challenge, I was given a web application that allows users to create custom frog avatars on an HTML5 canvas. 
When I first logged into it, I had to zoom out of my browser window so that it would allow me to view the site. This was an interesting start to the challenge. 

After analyzing the layout of the web application, I found that it was using an Nginx reverse proxy to forward user share requests to an administrative bot. I then discovered a potential parameter pollution flaw in how the proxy handles parameters. I was able
to append a payload onto an internal URL path.

The only trouble was the site had a Content Security Policy to prevent cross-site scripting. In order to get around this, I decided to wrap my payload in a local javascript pseudo-protocol in Firefox's DevTools. This allowed me to locally run a short fetch script to send a link to the admin bot.
Once the Chrome bot loaded my link, my script extracted the flag from its `localStorage` and uploaded it to the server's public API logs. From there, I simply visited the public API endpoint `/api/report/get` and copied the flag.