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

## Day 10: Thursday, January 12

**Today's Progress**: Big breakthrough! Using both the [Express/Sequelize example](https://github.com/sequelize/express-example) and the [chugg](https://github.com/TeamSmores/chugg) project I worked on at Codesmith as inspiration, I connected my database to my app without using express-generator. (I was reluctant to use the directory structure and files automatically generated by express-generator because I suspsected it was more than I needed, and I wanted to build my app from the ground up rather than using boilerplate I didn't fully understand yet.) The key was to create a put my Sequelize instance and models on an object exported by a module, which I could then import on my server file and anywhere else I needed it. (I still need to review exactly how modules work in Node - that would probably help me a lot going forward.)

I also separated my app into multiple modules, which should make it easier to work with as it grows.

**Thoughts**: Today definitely made up for yesterday. It felt great to see my database data in the browser, and to clean up my repo!

## Day 11: Friday, January 13

**Today's Progress**: I created a node file that, when executed, sends an SMS. I want it to create a database row too, but I'm getting SQL errors when I try to drop my database or save a new exchange.

**Thoughts**: Today was another slow day - I seem to be alternating between bad days (where I get stuck) and good ones (where I have a breakthrough). Hopefully the pattern will hold at least through tomorrow! I'm also feeling a bit burned out, so some sleep should help.

## Day 12: Sunday, January 15

**Today's Progress**: I fixed the node script so that it will create a row in the exchange table as well as send an SMS. I also realized some important things about my database:

Because each exchange is required to have a user...
* Before dropping the users table, I must drop the exchange table.
* Before deleting a specific user from the users table, I must delete any exchanges related to that user.

**Thoughts**: I felt guilty about taking a break yesterday and a bit distracted tonight (the holiday weekend is lovely, but now my schedule is out of whack, and I love my routines), but it was good to get back into the swing of things. Now the goal is momentum!

## Day 13: Monday, January 16

**Today's Progress**: I finished an MVP of start-exchange.js, which now does three things:
1. Create a message through Twilio (which then sends an SMS)
2. Create an exchange row in my database
3. Update the CurrentExchangeId of the corresponding user row in my database (I almost had this working yesterday, but I used an incorrect column name: 'currentExchangeId' rather than 'CurrentExchangeId')

I also refactored the script with promises to avoid the "pyramid of doom". A few key things I learned:
* When chaining promises, make sure each function in the chain returns a promise.
* A major benefit of promises is that you can handle all errors in one `catch` statement at the end of the chain, rather than handling errors separately for each function call. (That's what you'd have to do with callbacks.)

To make sure that I'd implemented my `catch` correctly, I tried causing errors in various functions throughout my promise chain. No matter where the error was, my `catch` statement seemed to work correctly.

**Thoughts**: I'm getting back in the groove of this project, and that feels good, though some days are more rewarding than others. I think I'll feel a pretty big sense of accomplishment when I start saving user responses to my database.

## Day 14: Tuesday, January 17

**Today's Progress**: I added a POST route to my app that receives message delivery updates from Twilio and updates my database accordingly. (I also accidentally cleared my database - be careful with forcing a database sync!)

**Thoughts**: It's exciting to see the different pieces of my app start to come together.

## Day 15: Wednesday, January 18

**Today's Progress**: I added a POST route that receives user responses and updates my database accordingly. It also sends the user a follow-up SMS thanking them for their response.

**Thoughts**: It's exciting to see complete exchanges in my database! However, there are several questions I still need to address. What if the user's response spans multiple text messages? How can I be certain that the SMS I receive from a user is really a response to the question I just sent? In particular, how can I confirm that the user sent their response after receiving my question? Should the "thank you" message be considered part of the exchange?

## Day 16: Thursday, January 19

**Today's Progress**: Today was more of a research day than a code-writing day. I looked into the Twilio API (using `curl | pbcopy` - pretty nifty) to see how close I could get to knowing when each question I'm sending is delivered and when each answer I receive is sent. There is some information available on the Message resource, but Twilio doesn't send it to me when I receive an inbound message or an outbound message delivery update. Rather than making an API request for this information, which is incomplete anyway, I'll log when I receive delivery confirmations for outbound messages and when I receive inbound messages from Twilio.

To start, I added a questionDeliveryConfirmedAt column to the Exchange model and wrote a migration to update my old exchanges.

**Thoughts**: I didn't get as much done today as I'd hoped, but it was good to practice Terminal commands and migrations. I'm still wrapping my head around when migrations are necessary and what exactly sequelize.sync does.

### Goals
1. Revise updateExchange.saveStatus to save questionDeliveryConfirmedAt
2. Revise /answer route to confirm that answer is received after questionDeliveryConfirmedAt
3. Use a linked-list-type structure to hold responses.

* Determine whether I need the config and models folders created when I ran sequelize init
* Understand when to run migrations and when to just update my model definitions and sync
* Add Q&A delivery times to exchange model?
* Flesh out isOrderCorrect
* Prevent responses from overriding one another
* Understand why I'm not seeing all my post requests in the Twilio console, even though I know these requests are happening, because they're updating the database.
* Understand how to use curl and pbcopy together
* Understand at what point I should respond with a 200 code
* Update the appropriate exchange when I receive a response
* Handle the case where a response spans multiple SMSs
* Figure out a more elegant way to trigger start-exchange.js
* Start saving real messages
* Start saving real users
* Triage todos
* Understand how node modules are imported and exported more deeply
* Understand promises better - which flavor should I start with?
* Understand this: Why is there a short pause between when a node script finishes executing (or at least when I see the last log) and when I see my command prompt in Terminal again?
* Understand approaches for organizing the require statements at the top of a script
* Later: discard npm modules I'm not using
* Later: Try Phoenix Framework if throughput is high

### Resource that may be useful
* [Twilio conversation](https://www.twilio.com/docs/guides/sms/how-to-create-sms-conversations-in-node-js)
* [Express/Sequelize example](https://github.com/sequelize/express-example)
* [Express/Sequelize explanation](http://docs.sequelizejs.com/en/1.7.0/articles/express/#implementing-a-todo-app)
* [Express application generator](https://expressjs.com/en/starter/generator.html)
