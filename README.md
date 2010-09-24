eventualj
====================

Eventual assertions, for Java.
Making asynchronous assertions elegant.

What is eventualj
---------------------
eventualj is an extension for [hamcrest's](http://code.google.com/p/hamcrest/) *Matchers* that allows support for matching values that are time dependent.
Often you will come across such scenarios when testing multithreaded applications.

Imagine the scenario where your application consumes messages from queues asynchronously. You want to test that when you put a message on the inbound queue it gets consumed. Because the message is consumed asynchronous you can't write an immediate assertion. Wouldn't it be nice if you could just write:

`whenIPutAMessageOnThe(inboundQueue);
assertThat(eventually(inboundQueue).isEmpty(), willBe(true));`


Examples
---------------------

`assertThat(eventually(ten()).getValue(), willBe(10)); // passes`

`assertThat(ten().getValue(), is(10)); // fails, ten()'s value hasn't been set yet`

`assertThat(eventually(messageQueue).isEmpty(), willBe(true).within(millis(100))); // passes eventually`