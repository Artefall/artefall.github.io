---
layout: post
title:  "Observer pattern. JS implementation"
date:   2021-06-04 12:00:00 +0200
---

Today I want to consider Observer pattern and show you implementation of this pattern in JavaScript.
What is Observer?

Observer is a classic design pattern, that represents relationship between publisher and subscriber entity (pub-sub briefly. Also, lots of developers refer to Observer pattern by calling it “pub-sub”).

So, who is observer and who is listener. In short — Listener subscribes on Observer and reacts on Observer’s notifications.

We can compare it with radio station. Radio station will broadcast regardless of whether you listening or not. But if you listen radio station, you achieve some information you can operate with. In Observer terms, radio station is a publisher, when you are a subscriber. Observer pattern is refer to reactive programming.
How observer is implemented

As I have said below, we need two classes to implement this pattern: Publisher and Subscriber. Publisher stores subscribers and call their callbacks, when notify method is called on Publisher.
JavaScript code

Let’s implement Observer pattern on JavaScript.

Publisher.js:

Subscriber.js:

index.js
Explanations

Steps to implement Publisher.js:

    Create storage of subscribers.
    Implement subscribe(name, callback) method. Method adds new listener to set.
    Implement describe(name) method. Method removes listener from set by name.
    Implement notify(message) method. Method executes notify method for every listener, passing specified message.

Steps to implement Subscriber.js:

    Create attribute for name and callback, that will execute when notify(message) method called.
    Implement notify(message) method, that executes listeners callback, passing message parameter.

At index.js file we declare Publisher and subscribe three different listeners. Then we call observer’s notify method with message “Test string number one”. Then we unsubscribe third listener, to check, whether describe method works or not. Call notify method again. Start the program.

As we see, three listeners was successfully subscribed and third was successfully described!
Congratulations!

Today we have reviewed and implemented Observer (pub-sub) pattern in JavaScript!

Thanks for reading!

I will be grateful if you support me on Patreon or Boosty

Follow me on telegram: https://t.me/secretsupper (most part of content could be found exactly in telegram).

Follow me on twitter: https://twitter.com/MaksymovArtem