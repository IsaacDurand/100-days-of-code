# 100 Days Of Code - Log

### Day 1: Tuesday, January 3

**Today's Progress**: I set up a Twilio account and practiced using it to send and receive text messages. I used [these docs](https://www.twilio.com/docs/quickstart/node/programmable-sms
).

**Thoughts**: It's really fun to be starting a project from scratch again but also a bit scary. I'm trying to remind myself that it's OK not to know up front exactly how all the technologies I'm using work or exactly what the finished product will look like; I'll figure this out as I go. The important thing is not how quick or direct the journey is but simply that I move forward or learn something new every day.

**Link(s) to work**
1. [Daily Digest](https://github.com/IsaacDurand/daily-digest)

### Day 2: Wednesday, January 4

**Today's Progress**: Building on the Express server I started yesterday, I created a simple web page with a form that accepts a user input and sends it to the back end.

**Thoughts**: It was nice to review Express and HTML forms because I'm a bit rusty on those. I like that HTML forms allow the user to submit information in multiple ways (e.g., hitting the Enter key rather than clicking), but I'm also remembering why so many devs dread them - it's inconvenient to have to override the default page-refreshing behavior of a submit event.

**Link(s) to work**
1. [Daily Digest](https://github.com/IsaacDurand/daily-digest)

### Day 3: Thursday, January 5

**Today's Progress**: I beefed up my server a bit. Now, when it receives text from the form on my webpage, it sends me that text as an SMS. And whenever I start my server, it prints a list of SMS messages associated with my Twilio account. I also set up Request Bin so that I can see confirmation messages when my SMSs are successfully delivered.

**Thoughts**: The first thing I did today - sending an SMS via an HTML form - was pretty easy. The second part - getting a confirmation message when the SMS is successfully delivered - was a bit harder. I wanted to send a confirmation message to my server, but I needed a URL for Twilio to contact, and my server is not deployed. I played with surge.sh (which doesn't let you deploy a server) and Request Bin (which received status updates from Twilio but couldn't communicate them with my server) before realizing that ngrok would do the trick. The key was understanding that I could stop and start my server without changing my ngrok URL.

### Interim goals
* Store my sent and received messages. First in Firebase and then in Redis or a more robust SQL database (I don't need speed)?
* Try Phoenix Framework if throughput is high
