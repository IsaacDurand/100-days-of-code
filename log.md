# 100 Days Of Code - Log

**Link(s) to work**
1. To start, I am working on a personal project called [Daily Digest](https://github.com/IsaacDurand/daily-digest).

### Day 1: Tuesday, January 3

**Today's Progress**: I set up a Twilio account and practiced using it to send and receive text messages. I used [these docs](https://www.twilio.com/docs/quickstart/node/programmable-sms
).

**Thoughts**: It's really fun to be starting a project from scratch again but also a bit scary. I'm trying to remind myself that it's OK not to know up front exactly how all the technologies I'm using work or exactly what the finished product will look like; I'll figure this out as I go. The important thing is not how quick or direct the journey is but simply that I move forward or learn something new every day.

### Day 2: Wednesday, January 4

**Today's Progress**: Building on the Express server I started yesterday, I created a simple web page with a form that accepts a user input and sends it to the back end.

**Thoughts**: It was nice to review Express and HTML forms because I'm a bit rusty on those. I like that HTML forms allow the user to submit information in multiple ways (e.g., hitting the Enter key rather than clicking), but I'm also remembering why so many devs dread them - it's inconvenient to have to override the default page-refreshing behavior of a submit event.

### Day 3: Thursday, January 5

**Today's Progress**: I beefed up my server a bit. Now, when it receives text from the form on my webpage, it sends me that text as an SMS. And whenever I start my server, it prints a list of SMS messages associated with my Twilio account. I also set up Request Bin so that I can see confirmation messages when my SMSs are successfully delivered.

**Thoughts**: The first thing I did today - sending an SMS via an HTML form - was pretty easy. The second part - getting a confirmation message when the SMS is successfully delivered - was a bit harder. I wanted to send a confirmation message to my server, but I needed a URL for Twilio to contact, and my server is not deployed. I played with surge.sh (which doesn't let you deploy a server) and Request Bin (which received status updates from Twilio but couldn't communicate them with my server) before realizing that ngrok would do the trick. The key was understanding that I could stop and start my server without changing my ngrok URL.

### Day 4: Friday, January 6

**Today's Progress**: I updated my server to log text messages sent via Twilio, text messages received via Twilio, and text message delivery notifications from Twilio. Right now, I'm just writing this data to a text file using Node's fs module. The next step is to use a database - I'm excited!

**Thoughts**: A lot of the code I wrote today likely won't appear in the finished version of my project, but I think this work helped me get more comfortable with Twilio's REST API. I also think I'm doing a pretty good job of breaking this project into small pieces and tackling them one at a time. It's really nice to have the freedom to work slowly - to be able to dive deeply into concepts I want to understand better, without feeling guilty about going down a rabbit hole! Thinking forward, it may be difficult to link an outbound question SMS with its associated inbound response - I don't think the free version of Twilio's API provides the concept of a "conversation".

## Day 5: Saturday, January 7

**Today's Progress**: I set up a MySQL database to store my messages. I also connected to it from my server using the Sequelize ORM.

**Thoughts**: I didn't write much code today, but I think I made a bit of progress wrapping my head around how databases work and how apps interact with them. These are topics I really want to learn more about, so I'm glad I'm exploring them, even though they make my head hurt. :)

## Day 6: Sunday, January 8

**Today's Progress**: I used Sequelize to create a user table and add rows to it.

**Thoughts**: Today was another day where I read more than I wrote, but I'm really enjoying this opportunity to revisit the fundamentals of databases. The hour flew by! I'm also trying to remind myself that it's OK to try things out in my code before I fully understand them and then read the docs or source code to understand why my code is or isn't working as I expect it to.

## Day 7: Monday, January 9

**Today's Progress**: I created an Exchange table and linked it to my User table. (I'm defining an exchange as one interaction between the app and the user, where the app asks a question and the user answers it.)

**Thoughts**: I'm working on wrapping my head around associations and foreign keys. Would I learn these concepts better if I used raw SQL instead of Sequelize, even though that would be more difficult and probably not as secure or production-friendly? I'm also noticing that there is a lot of overlap between the different sections of the Sequelize documentation, and it can be hard to know which section will be most useful. It would be helpful if I could find some better documentation for MySQL too. This process feels slow, but I do think I'm learning a lot!

## Day 8: Tuesday, January 10

**Today's Progress**: I practiced creating exchange and users instances and linking them to one another.

**Thoughts**: Most of the code I wrote today probably won't end up in the finished project, and I still don't love playing around with Sequelize without fully understanding what's going on, but getting my hands dirty is probably the best way to learn. I'd like to get a better sense of what exists on my server (instances) and what exists in the database (rows). I'd also like to review promises and best practices (like the best way to chain them) so that I don't end up creating an unmanageable Russian doll.

## Day 9: Wednesday, January 11

**Today's Progress**: When I started coding today, I had a server (created with Express) and a database connection (created with Sequelize), but I wasn't sure how to bring them together so that my app could interact with the database. For help, I did some Googling with the search terms "Express" and "Sequelize", and I found some resources (below) that I'm starting to walk through.

**Thoughts**: I'm feeling a bit discouraged because I didn't make as much progress today as I'd hoped, and I was already feeling tired. I'm trying to remind myself that the important thing is how consistently I'm working on this app, not how quickly I get it done. After all, one of the goals of this project is to give me an opportunity to slow down and really understand everything I'm doing! And I suppose it's a good thing to be moving beyond Express's "hello world" example.

### Resource that may be useful
* [Express/Sequelize example](https://github.com/sequelize/express-example)
* [Express/Sequelize explanation](http://docs.sequelizejs.com/en/1.7.0/articles/express/#implementing-a-todo-app)
* [Express application generator](https://expressjs.com/en/starter/generator.html)

### Goals
* **Understand what happens when I run** `daily-debrief/bin/www`
* Move createExampleUsers to its own file
* Remove files/folders created by express-generator that I don't need
* Move the routing and the database setup into different files?
* Start saving real messages
* Start saving real users
* Later: Try Phoenix Framework if throughput is high
