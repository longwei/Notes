Web Scraping or How to pull data from a website without API

“If it can bleed, I can kill it.” Just kidding, if the website provide a way for download HTML content and render it in your brower, then the content could be accessed via script. Don’t wasting your time repeatly doing thing for hours that can be done in script in few minutes.

Note: decent website normally provide APIs for fetch data, which make thing really really easy. all you need to do, is to read the document and find the section that you interested in. then to register a key and then send along the key with every request.

let’s make some fun.

define the data, and figure out basic access patterns This is the most important and comfusing part. each website has their own unstructed data. Here are few question to define the data a. what is the endpoint, which in human language, where is the url that return the data. b. what is the GET parameters? What if the data is fetched by POST method? huh?? Yes, it did happens. b1. find the form, get the action attribute and sending data variable name; b2. setup a localhost, print receive post request, then redirect the form action attribute to your localhost b3. then verified your post request. cUrl is your friend to spoof a http request. http://curl.haxx.se/docs/httpscripting.html if tl:tr, here is the shortcut –location for redirection –data for post request data
What if the the data is fetched by ajax? capture your xhr request, then spoof it.

What if the html page is unstructed? 1. find the CSS hooks. which is the class attribute of

you interested in. this is normal way designer organize the webpage themself. 2. get a good html parsing library, dont use xml or dont even try to use REGEX.
Have fun, write a script to fire off a request to the url and pars the returned data. follow up, https://gist.github.com/gjreda/f3e6875f869779ec03db

Tips on debug: 1. Header sometime matters, try to copy the header exactly as you did in brower 2. Login? find a httop library that handles logins and send.

https://gist.github.com/longwei/5096906
