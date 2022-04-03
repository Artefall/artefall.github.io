---
layout: post
title:  "Observer pattern. JS implementation"
date:   2021-06-04 12:00:00 +0200
---

![welcome](images/2021/observer-pattern-js-implementation/welcome.jpeg)

Today I want to consider Observer pattern and show you implementation of this pattern in JavaScript.
What is Observer?

Observer is a classic design pattern, that represents relationship between publisher and subscriber entity (pub-sub briefly. Also, lots of developers refer to Observer pattern by calling it “pub-sub”).

So, who is observer and who is listener. In short — Listener subscribes on Observer and reacts on Observer’s notifications.

We can compare it with radio station. Radio station will broadcast regardless of whether you listening or not. But if you listen radio station, you achieve some information you can operate with. In Observer terms, radio station is a publisher, when you are a subscriber. Observer pattern is refer to reactive programming.
How observer is implemented

As I have said below, we need two classes to implement this pattern: Publisher and Subscriber. Publisher stores subscribers and call their callbacks, when notify method is called on Publisher.
JavaScript code

Let’s implement Observer pattern on JavaScript.

## Publisher.js:

![publisher](images/2021/observer-pattern-js-implementation/publisher.png)

## Subscriber.js:

![subscriber](images/2021/observer-pattern-js-implementation/subscriber.png)

## index.js

![index](images/2021/observer-pattern-js-implementation/index.png)

Explanations

Steps to implement Publisher.js:

1. Create storage of subscribers.
2. Implement subscribe(name, callback) method. Method adds new listener to set.
3. Implement describe(name) method. Method removes listener from set by name.
4. Implement notify(message) method. Method executes notify method for every listener, passing specified message.

Steps to implement Subscriber.js:

1. Create attribute for name and callback, that will execute when notify(message) method called.
2. Implement notify(message) method, that executes listeners callback, passing message parameter.

At index.js file we declare Publisher and subscribe three different listeners. Then we call observer’s notify method with message “Test string number one”. Then we unsubscribe third listener, to check, whether describe method works or not. Call notify method again. Start the program.

![start program](images/2021/observer-pattern-js-implementation/result.png)

As we see, three listeners was successfully subscribed and third was successfully described!
Congratulations!

{% include farewell.md conclusion="Today we have reviewed and implemented Observer (pub-sub) pattern in JavaScript!
" %}

