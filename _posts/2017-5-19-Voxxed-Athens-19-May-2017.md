Today I attended [Voxxed Days Athens](https://voxxeddays.com/athens/) and had a great time. This post contains the quick notes I took at the talks I went to.

## The art of visualising software architecture (Simon Brown)

The [keynote speech](https://voxxeddays.com/athens/sessions/visualising-software-architecture/) was by [Simon Brown](https://voxxeddays.com/athens/speakers/simon-brown/), who started his presentation by pointing out the disparity and lack of standardisation of software architecture diagrams (functional view, component view). Members of the same team will draw the same system they just architected together differently and will not understand each other's diagram. He went on with some different software visualisation approaches and their disadvantages describing architecture. For example, UML (which is too low level), N+1 and the methodologies in the book View points and perspectives. Almost always the Logical view  and the Development view are different, because they are created by different people with different viewpoints (i.e. Business vs Architect). 

The problem is that there is no good, ubiquitous vocabulary to describe software architecture. The so called "Component diagrams" all around the world have a different level of abstraction (he showed a diagram with a cryptic "Business Logic" component). He also listed some desired properties for a diagramming model:

* To be text-based (in order to be version-controllable and diffable)
* To be connected to the code

Simon brown has created his own software system diagram, [Structurizr](https://www.structurizr.com/), which has 4 levels of abstraction: Software system > Containers > Components > Classes. It is a static model around which all sorts of views can be created. Structurizr comes with 2 libraries (one for Spring and one for .Net), which scan a compiled project with reflection and generate the text model for the software. You can have a look at some of the diagrams that can be created out of the generated model [here](https://www.structurizr.com/help/examples). Some of these, have "drill-down" capabilities from the high-level to the lower-level layers of the architecture. 

## You can do better with Kotlin (Svetlana Isakova)

Next I attended the [talk](https://voxxeddays.com/athens/sessions/you-can-do-better-with-kotlin/) about Kotlin by [Svetlana Isakova](https://voxxeddays.com/athens/speakers/svetlana-isakova/) of Jetbrains, which is [as of yesterday](https://blog.jetbrains.com/kotlin/2017/05/kotlin-on-android-now-official/) officially supported for Android development. Kotlin compiles to Java bytecode, to Javascript and native code. Also, Gradle plans to support Kotlin. Thanks to Jetbrains (who also develops one of the best IDEs), it also has very good tooling (she also showed us the Java to Kotlin converter). She then went on with some important features of the language, like the named method parameters, the data keyword (which adds equals and hashcode methods to classes) and the nullable types. She spent the rest of the talk on coroutines, one of the (experimental for now) features of the language, which provides the language constructs for async-await.

## Continuous learning of Tech Professionals in an evolving world (Dimitris Livas)

The next [talk](https://voxxeddays.com/athens/sessions/continuous-learning-tech-professionals-evolving-world/) I attended was by [Dimitris Livas](https://voxxeddays.com/athens/speakers/dimitris-livas/), and was about the important role of continuous learning of tech professionals in a world that evolves with great speed. He started by exploring the needs of a professional in order to remain relevant (i.e. to be marketable, up-to-date) and the needs of businesses (to be attractive to talent, to be able to migrate its tech). As far as professionals are concerned, common challenges are self awareness, field state awareness and the adaptation to new evolving stages. Also, different professionals have different goals (i.e. long term employment, or using bleeding edge technology, or set a target role for the next years). 

A key takeaway from the talk was that the term "scrumification" is applicable for the personal development of a professional (where the professional is the scrum master and product owner, their personal development is the product and the things they want to grow into are the backlog). The professional development also has "sprints", as it involves small steps, reevaluation of targets and keeping track of the progress. 

Dimitris Livas also pointed out the importance to have a coach, who works on the same area with the goals of the professional. Finally, he closed with five values that are essential for the personal development: Having a purpose, being adventurous, being agile, respecting and empowering colleagues and trust.

## Taming the Dragon: Conquering non blocking code with RxJava (Frank Lyaruu)

I then attended the [talk](https://voxxeddays.com/athens/sessions/taming-the-dragon-conquering-non-blocking-code-with-rxjava/) by [Frank Lyaruu](https://voxxeddays.com/athens/speakers/Frank-Lyaruu/) on RxJava. Frank started by listing the merits of blocking code over non-blocking: it is familiar, easy to reason about and easy to debug. He went on by comparing the same code in non-blocking servlet 3.1 (>30 lines) versus node.js (3 lines). He went on with RxJava and wrapped some blocking code in a non-blocking method returning an Observable, showing that it is light and easy to add to existing apps. He also touched the notion of backpressure.

Frank continued by clearing out that non-blocking code is not about running faster, but rather unblocking threads, and pointed out that there are few reactive drivers available (i.e. RxNetty, RxMongo, Couchbase, barely any SQL support). Furthermore, he underlined that blocking IO is a lie, but you can get away with it if network latecy is low (however, applications cover more distance) and if our network is reliable (however, we use wireless more and more).

He closed concluding that blocking code misbehaves under pressure and that its price will keep going up. So the adoption of non-blocking code will be inevitable.

## Mutation Testing to the rescue of your Tests (Nicolas Frankel)

This was my favourite technical [talk](https://voxxeddays.com/athens/sessions/mutation-testing-rescue-tests/) of the conference, by [Nicolas Frankel](https://voxxeddays.com/athens/speakers/Nicolas-Frankel/), and was about mutation testing. Apart from the interesting topic, the talk had just the right amount of developer grievances and humour. Nicolas started with listing the many kinds of testing that we use (unit, integration, performance, penetration, end-to-end and others) trying to ensure the quality of our production code. He pointed out that one of the metrics we most often use is code coverage, and we often fool ourselves that high code coverage alone means quality code, which is not the case given how easy it is to achieve high code coverage without testing anything of value.
 
 He then went on by explaining what mutation testing is. Mutation testing in essence messes up our code in different ways (how cool is that!) and makes sure that our normal tests fail. If the tests don't fail on the messed up code, there is something wrong. He went on with [PIT](http://pitest.org/) and the list of [mutations](http://pitest.org/quickstart/mutators/) it supports. Some important ones are the "conditionals boundary mutator" (it you have `if (a<b) {...}` the mutator may change it to `if (a<=b) {...}`), removing method calls and others.
 
 Nicolas went on with a demo, and closed saying that PIT comes with its own set of shortcomings. For example, it does produce false positives, it is slow (it will create a new version of the code for each applied mutation, run all the tests on it and produce aggregate results). Some of these shortcomings have workarounds, like using more threads, incremental analysis (i.e. running mutation tests only for changed code), and not binding to the test phase. 



## Better security and privacy for your web apps (Panos Astithas)

Next on my schedule was the [talk](https://voxxeddays.com/athens/sessions/better-security-privacy-web-apps/) by [Panos Astithas](https://voxxeddays.com/athens/speakers/panos-astithas/) on better security and privacy for web apps. Panos started by underlying that privacy and security are more important than ever, and people have began caring. 

He started with encryption, pointing out the "good parts" of the last years: HTTP/2, TLS 1.3, HTTP Strict Transport Security, HTTP Public Key Pinning and most importantly [Let's Encrypt](https://letsencrypt.org/), which is backed by many companies, is free and tries to be transparent. He went on with the not so good parts: insecure algorithms, missing intermediate CA certificates (~6% of HTTPS requests on FF), mixed content (passive vs active) and insecure logins (~25%).

Panos then went on with the tools we have on Content security:

* For cookies we have useful directives, such as `Expires` and `Max-Age`, `Secure` and `HttpOnly`, `Domain` and `Path`. Also, experimental directives (supported in Firefox) such as `__Secure-` and `__Host-`. 
* The Content Security Policy HTTP header can be used to limit the places our resources can come from. 
* He also mentioned the experimental [Web Crypto API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API)
* Cross Origin Resource sharing and Subresource Integrity.
* For permissions on the web (for geolocation and notifications, push and WebRTC) he mentioned the [Permissions API](https://developer.mozilla.org/en-US/docs/Web/API/Permissions_API)
* Best practices: avoid the load event, pre-prompt for context, prefer HTTPS, prompt in parent frames

He finished his talk with some points on Privacy:

* tracking erodes trust (users only trust the first party to track them, and not third parties), that Ad networks can serve malware, and that there is a differentiation between tracking protection versys ad blockers. 
* Tracking mitigations: tracking scripts may fail to load, sendBeacon vs onBeforeUnload, anti-fingerprinting, lean data practices (https://www.mozilla.org/en-US/about/policy/lean-data/)
* Internet health report (https://internethealthreport.org/v01/)
* Observatory (https://observatory.mozilla.org/)


## Numbers (Douglas Crockford)

The [closing keynote](https://voxxeddays.com/athens/sessions/numbers/) was by the well known [Douglas Crockford](https://voxxeddays.com/athens/speakers/douglas-crockford/).


## Conclusion

International IT conferences were not part of our life in Athens. Voxxed Days was a very pleasant addition to our lives. Not everything around it was perfect, but the conference was overall very successful. Lots of people (~450) attended and had a good time, exchanged ideas, learning interesting things. Now that Voxxed Days was held, we should support it so that it can come back next year with more talks and more attendees. 

So, cheers to the team! I am looking forward to it.

