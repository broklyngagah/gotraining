## Ultimate Go

This is material for any intermediate-level developer who has at least a few months to years of experience writing code in Go. This class provides a very deep knowledge of the programming langauge with a big push on language mechanics, design philosophies and guidelines. We focus on teaching how to write code with a priority on consistency, integrity, readability and simplicity. We cover a lot about “if performance matters” with a focus on mechanical sympathy, data oriented design, decoupling and writing production software. We close the class with benchmarking, profiling, tracing and debugging. If you want your team to be better Go developers, code reviewers, designers and architects, this is the class they need.

[Ultimate Go](../courses/go/README.md)

## Design Guidelines

You must develop a design philosophy that establishes a set of guidelines. This is more important than developing a set of rules or patterns you apply blindly. Guidelines help to formulate, drive and validate decisions. You can't begin to make the best decisions without understanding the impact of your decisions. Every decision you make, every line of code you write comes with trade-offs.

* [Prepare Your Mind](https://github.com/ardanlabs/gotraining/tree/master/topics/go#prepare-your-mind)
* [Productivity vs Performance](https://github.com/ardanlabs/gotraining/tree/master/topics/go#productivity-vs-performance)
* [Correctness vs Performance](https://github.com/ardanlabs/gotraining/tree/master/topics/go#correctness-vs-performance)
* [Code Reviews](https://github.com/ardanlabs/gotraining/tree/master/topics/go#code-reviews)
* [Data Oriented Design](https://github.com/ardanlabs/gotraining/tree/master/topics/go#data-oriented-design)
* [Interface And Composition Design](https://github.com/ardanlabs/gotraining/tree/master/topics/go#interface-and-composition-design)
* [Package Oriented Design](https://github.com/ardanlabs/gotraining/tree/master/topics/go#package-oriented-design)
* [Concurrent Software Design](https://github.com/ardanlabs/gotraining/tree/master/topics/go#concurrent-software-design)
* [Channel Design](https://github.com/ardanlabs/gotraining/tree/master/topics/go#channel-design)

---

### Prepare Your Mind

**Somewhere Along The Line**  
* We became impressed with programs that contain large amounts of code.
* We strived to create large abstractions in our code base.
* We forgot that the hardware is the platform.
* We lost the understanding that every decision comes with a cost.

**These Days Are Gone**  
* We can throw more hardware at the problem.
* We can throw more developers at the problem.

**Aspire To**  
* Be a champion for quality, efficiency and simplicity.
* Have a point of view.
* Value introspection and self-review.

**Open Your Mind**  
* Technology changes quickly but people's minds change slowly.
* Easy to adopt new technology but hard to adopt new ways of thinking.

---

### Legacy Software

Do you care about the legacy you are leaving behind?

_"There are two kinds of software projects: those that fail, and those that turn into legacy horrors." - Peter Weinberger (inventor of AWK)_

_"Legacy software is an unappreciated but serious problem. Legacy code may be the downfall of our civilization." - Chuck Moore (inventor of Forth)_

---

### Productivity vs Performance

Productivity and performance both matter, but in the past you couldn’t have both. You needed to choose one over the other. We naturally gravitated to productivity, with the idea or hope that the hardware would resolve our performance problems for free. This movement towards productivity has resulted in the design of programming languages that produce sluggish software that is out pacing the hardware’s ability to make them faster.

By following Go’s idioms and a few guidelines, we can write code that can be reasoned about by anyone who looks at it. We can write software that simplifies, minimizes and reduces the amount of code we need to solve the problems we are working on. We don’t have to choose productivity over performance or performance over productivity anymore. We can have both.

**Quotes**

_"The hope is that the progress in hardware will cure all software ills. However, a critical observer may observe that software manages to outgrow hardware in size and sluggishness. Other observers had noted this for some time before, indeed the trend was becoming obvious as early as 1987." - Niklaus Wirth_

_"The most amazing achievement of the computer software industry is its continuing cancellation of the steady and staggering gains made by the computer hardware industry." - Henry Petroski (2015)_

_"The hardware folks will not put more cores into their hardware if the software isn’t going to use them, so, it is this balancing act of each other staring at each other, and we are hoping that Go is going to break through on the software side.” - Rick Hudson (2015)_

_"C is the best balance I've ever seen between power and expressiveness. You can do almost anything you want to do by programming fairly straightforwardly and you will have a very good mental model of what's going to happen on the machine; you can predict reasonably well how quickly it's going to run, you understand what's going on .... - Brian Kernighan (2000)_

_"The trend in programming language design has been to create languages that enhance software reliability and programmer productivity. What we should do is develop languages alongside sound software engineering practices so the task of developing reliable programs is distributed throughout the software lifecycle, especially into the early phases of system design." - Al Aho (2009)_

---

### Correctness vs Performance

You want to write code that is optimized for correctness. Don't make coding decisions based on what you think might perform better. You must benchmark or profile to know if code is not fast enough. Then and only then should you optimize for performance. This can't be done until you have something working.

Improvement comes from writing code and thinking about the code you write. Then refactoring the code to make it better. This requires the help of other people to also read the code you are writing. Prototype ideas first to validate them. Try different approaches or ask others to attempt a solution. Then compare what you have learned.

Too many developers are not prototyping their ideas first before writing production code. It is through prototyping that you can validate your thoughts, ideas and designs. This is the time when you can break down walls and figure out how things work. Prototype in the concrete and consider contracts after you have a working prototype.

Refactoring must become part of the development cycle. Refactoring is the process of improving the code from the things that you learn on a daily basis. Without time to refactor, code will become impossible to manage and maintain over time. This creates the legacy issues we are seeing today.

**Quotes**

_"The correctness of the implementation is the most important concern, but there is no royal road to correctness. It involves diverse tasks such as thinking of invariants, testing and code reviews. Optimization should be done, but not prematurely." - Al Aho (inventor of AWK)_

_"The basic ideas of good style, which are fundamental to write clearly and simply, are just as important now as they were 35 years ago. Simple, straightforward code is just plain easier to work with and less likely to have problems. As programs get bigger and more complicated, it's even more important to have clean, simple code." - Brian Kernighan_

_"Unless the developer has a really good idea of what the software is going to be used for, there's a very high probability that the software will turn out badly. If the developers don't know and understand the application well, then it's crucial to get as much user input and experience as possible." - Brian Kernighan_

_"The hardest bugs are those where your mental model of the situation is just wrong, so you can't see the problem at all" - Brian Kernighan_

_"Everyone knows that debugging is twice as hard as writing a program in the first place. So if you're as clever as you can be when you write it, how will you ever debug it?" - Brian Kernighan_

**Resources:**

[Prototype your design!](https://www.youtube.com/watch?v=vLxX3yZmw5Q) - Robert Griesemer

---

### Code Reviews

You can't look at a piece of code, function or algorithm and determine if it smells good or bad without a design philosophy. These four major categories are the basis for code reviews and should be prioritized in this order: Integrity, Readability, Simplicity and then Performance. You must consciously and with great reason be able to explain the category you are choosing.

_"The software business is one of the few places we teach people to write before we teach them to read". - Tom Love (inventor of Objective C)_

---

### Integrity

**_We need to become very serious about reliability._**

There are two driving forces behind integrity:  
* Integrity is about every allocation, read and write of memory being accurate, consistent and efficient. The type system is critical to making sure we have this `micro` level of integrity.
* Integrity is about every data transformation being accurate, consistent and efficient. Writing less code and error handling is critical to making sure we have this `macro` level of integrity.

**Write Less Code:**

There have been studies that have researched the number of bugs you can expect to have in your software. The industry average is around 15 to 50 bugs per 1000 lines of code. One simple way to reduce the number of bugs, and increase the integrity of your software, is to write less code.

Bjarne Stroustrup stated that writing more code than you need results in `Ugly`, `Large` and `Slow` code:

* `Ugly`: Leaves places for bugs to hide.
* `Large`: Ensures incomplete tests.
* `Slow`: Encourages the use of shortcuts and dirty tricks.

**Error Handling:**

When error handling is treated as an exception and not part of the main code, you can expect the majority of your critical failures to be due to error handling.

48 critical failures were found in a study looking at a couple hundred bugs in Cassandra, HBase, HDFS, MapReduce, and Redis.  
* 92% : Failures from bad error handling
    * 35% : Incorrect handling
        * 25% : Simply ignoring an error
        * 8% : Catching the wrong exception
        * 2% : Incomplete TODOs
    * 57% System specific
        * 23% : Easily detectable
        * 34% : Complex bugs
* 8% : Failures from latent human errors

**Ignorance vs Carelessness:**

Anytime we identify an integrity issue we need to ask ourselves why it happened.
```
                    Not Deliberate               Deliberate
              ------------------------------------------------------
              |                          |                         |
              |                          |                         |
   Ignorance  |  Learning / Prototyping  |    Hacking / Guessing   |
              |                          |                         |
              |                          |                         |
              |-----------------------------------------------------
              |                          |                         |
              |                          |                         |
Carelessness  |        Education         |   Dangerous Situation   |
              |                          |                         |
              |                          |                         |
              ------------------------------------------------------
```
**Resources:**

[Software Development for Infrastructure](http://www.stroustrup.com/Software-for-infrastructure.pdf) - Bjarne Stroustrup  
[Normalization of Deviance in Software](http://danluu.com/wat/) - danluu.com  
[Lessons learned from reading postmortems](http://danluu.com/postmortem-lessons/) - danluu.com  
[Technical Debt Quadrant](https://martinfowler.com/bliki/TechnicalDebtQuadrant.html) - Martin Fowler  
[Design Philosophy On Integrity](https://www.goinggo.net/2017/02/design-philosophy-on-integrity.html) - William Kennedy  
[Ratio of bugs per line of code](https://www.mayerdan.com/ruby/2012/11/11/bugs-per-line-of-code-ratio) - Dan Mayer  
[Masterminds of Programming](http://dl.acm.org/citation.cfm?id=1592983) - Federico Biancuzzi and Shane Warden  
[Developing Software The Right Way, with Intent and Carefulness](http://ipengineer.net/2017/04/developing-software-the-right-way-with-intent-and-carefulness) - David Gee  

---

### Readability

**_We must structure our systems to be more comprehensible._**

This is about writing simple code that is easy to read and understand without the need of mental exhaustion. Just as important, it's about not hiding the cost/impact of the code per line, function, package and the overall ecosystem it runs in.

[Example Readability Issue](http://cpp.sh/6i7d)  

**Real Machine**

_"A well-designed language has a one-one correlation between source code and object code. It's obvious to the programmer what code will be generated from their source. This provides its own satisfaction, is efficient, and reduces the need for documentation." - Chuck Moore (inventor of Forth)_

In Go, the underlying machine is the real machine rather than a single abstract machine. The model of computation is that of the computer. Here is the key, Go gives you direct access to the machine while still providing abstraction mechanisms to allow higher-level ideas to be expressed.

**Mental Models**

_"Let's imagine a project that's going to end up with a million lines of code or more. The probability of those projects being successful in the United States these days is very low - well under 50%. That's debatable. - Tom Love (inventor of Objective C)_

_100k lines of code fit inside a box of paper. - Tom Love (inventor of Objective C)_

How much code in that box do you think you can maintain a mental model of in your head? I believe asking a single developer to maintain a mental model of more than one ream of paper in that box (~10k lines of code) is asking a lot. If you do the math, then it takes a team of 100 people to work on a code base that hits a million lines of code. That is 100 people that need to be coordinated, grouped, tracked and in a constant feedback loop of communication.

**Average Developer**

_"Can you explain it to the median user (developer)? as opposed to will the smartest user (developer) figure it out?" - Peter Weinberger (inventor of AWK)_

You must be aware of who you are on your team. When hiring new people, you must be aware of where they fall. The code must be written for the average developer to comprehend. If you are below average, you have the responsibility to come up to speed. If you are the expert, you have the responsbility to reduce being clever.

---

### Simplicity

**_We must understand that simplicity is hard to design and complicated to build._**

This is about hiding complexity. A lot of care and design must go into simplicity because this can cause more problems then good. It can create issues with readability and it can cause issues with performance.

**Simple, But Not Simpler**

_"Everything should be made as simple as possible, but not simpler." - Albert Einstein_

Focus on encapsulation and validate that you're not generalizing or even being too concise. You might think you are helping the programmer or the code but validate things are still easy to use, understand, debug and maintain.

**Encapsulation**

_Paraphrasing: "Encapsulation and the separation of concerns are drivers for designing software. This is largely based on how other industries handle complexity. There seems to be a human pattern of using encapsulation to wrestle complexity to the ground." - Brad Cox (inventor of Objective C)_

Encapsulation is what we have been trying to figure out as an industry for 40 years. Go is taking a slightly new approach with the package. Brining encapsulation up a level and providing richer support at the language level.

**Resources:**

[Simplicity is Complicated](https://www.youtube.com/watch?v=rFejpH_tAHM) - Rob Pike  

---

### Performance

**_We must compute less to get the results we need._**

This is about not wasting effort and achieving execution efficiency. Writing code that is mechanically sympathetic with the runtime, operating system and hardware. Achieving performance by writing less and more efficient code but staying within the idioms and framework of the language.

_"Programmers waste enormous amounts of time thinking about, or worrying about, the speed of non-critical parts of their programs, and these attempts at efficiency actually have a strong negative impact when debugging and maintenance are considered. We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%." — Donald E. Knuth_

_"I don't trust anything until it runs... In fact, I don't trust anything until it runs twice." - Andrew Gelman (one of the greatest living statisticians at Columbia University)._

Rules of Performance:   
    * Never guess about performance.  
    * Measurements must be relevant.  
    * Profile before you decide something is performance critical.  
    * Test to know you are correct.

[Example Benchmark](https://github.com/ardanlabs/gotraining/blob/master/topics/go/testing/benchmarks/basic/basic_test.go)  

**Broad Engineering**

_"When we're computer programmers we're concentrating on the intricate little fascinating details of programming and we don't take a broad engineering point of view about trying to optimize the total system. You try to optimize the bits and bytes." - Tom Kurtz (inventor of BASIC)_

Performance is important but it can't be your priority unless the code is not running fast enough. You only know this once you have a working program and you have validated it. We place those who we think know how to write performant code on a pedestal. We need to put those who write code that is optimized for correctness and performs fast enough on those pedestals.

---

### Micro-Optimizations

Micro-Optimizations are about squeezing every ounce of performance as possible. When code is written with this as the priority, it is very difficult to write code that is readable, simple or idiomatic. You are writing clever code that may require the unsafe package or you may need to drop into assembly.

[Example Micro Optimization](https://play.golang.org/p/D_bImirgXL)

---

### Data-Oriented Design

**Design Philosophy:**

* If you don't understand the data, you don't understand the problem.
* All problems are unique and specific to the data you are working with.
* Data transformations are at the heart of solving problems. Each function, method and work-flow must focus on implementing the specific data transformations required to solve the problems.
* If your data is changing, your problems are changing. When your problems are changing, the data transformations needs to change with it.
* Uncertainty about the data is not a license to guess but a directive to STOP and learn more.
* Solving problems you don't have, creates more problems you now do.
* If performance matters, you must have mechanical sympathy for how the hardware and operating system work.
* Minimize, simplify and REDUCE the amount of code required to solve each problem. Do less work by not wasting effort.
* Code that can be reasoned about and does not hide execution costs can be better understood, debugged and performance tuned.
* Coupling data together and writing code that produces predictable access patterns to the data will be the most performant.
* Changing data layouts can yield more significant performance improvements than changing just the algorithms.
* Efficiency is obtained through algorithms but performance is obtained through data structures and layouts.

**Resources:**

[Data-Oriented Design and C++](https://www.youtube.com/watch?v=rX0ItVEVjHc) - Mike Acton  
[Efficiency with Algorithms, Performance with Data Structures](https://www.youtube.com/watch?v=fHNmRkzxHWs) - Chandler Carruth

---

### Interface And Composition Design

**Design Philosophy:**

* Interfaces give programs structure.
* Interfaces encourage design by composition.
* Interfaces enable and enforce clean divisions between components.
    * The standardization of interfaces can set clear and consistent expectations.
* Decoupling means reducing the dependencies between components and the types they use.
    * This leads to correctness, quality and performance.
* Interfaces allow you to group concrete types by what they do.
    * Don't group types by a common DNA but by a common behavior.
    * Everyone can work together when we focus on what we do and not who we are.
* Interfaces help your code decouple itself from change.
    * You must do your best to understand what could change and use interfaces to decouple.
    * Interfaces with more than one method have more than one reason to change.
    * Uncertainty about change is not a license to guess but a directive to STOP and learn more.
* You must distinguish between code that:
    * defends against fraud vs protects against accidents

**Validation:**

Use an interface when:  
* users of the API need to provide an implementation detail.
* API’s have multiple implementations they need to maintain internally.
* parts of the API that can change have been identified and require decoupling.

Don't use an interface:  
* for the sake of using an interface.
* to generalize an algorithm.
* when users can declare their own interfaces.
* if it's not clear how the interface makes the code better.

**Resources:**

[Methods, interfaces and Embedding](https://www.goinggo.net/2014/05/methods-interfaces-and-embedded-types.html) - William Kennedy  
[Composition with Go](https://www.goinggo.net/2015/09/composition-with-go.html) - William Kennedy  
[Reducing type hierarchies](https://www.goinggo.net/2016/10/reducing-type-hierarchies.html) - William Kennedy  
[Interface pollution in Go](https://medium.com/@rakyll/interface-pollution-in-go-7d58bccec275) - Burcu Dogan  
[Application Focused API Design](https://www.goinggo.net/2016/11/application-focused-api-design.html) - William Kennedy  
[Avoid interface pollution](https://www.goinggo.net/2016/10/avoid-interface-pollution.html) - William Kennedy  

---

### Package-Oriented Design

_Package Oriented Design allows a developer to identify where a package belongs inside a Go project and the design guidelines the package must respect. It defines what a Go project is and how a Go project is structured. Finally, it improves communication between team members and promotes clean package design and project architecture that is discussable._

[Learn More](design/packaging)

---

### Concurrent Software Design

Concurrency is about managing multiple things at once. Like one person washing the dishes while they are also cooking dinner. You're making progress on both but you're only ever doing one of those things at the same time. Parallelism is about doing multiple things at once. Like one person cooking and placing dirty dishes in the sink, while another washes the dishes. They are happening at the same time.

Both you and the runtime have a responsibility in managing the concurrency of the application. You are responsible for managing these three things when writing concurrent software:

**Design Philosophy:**

* The application must startup and shutdown with integrity.
    * Know how and when every goroutine you create terminates.
    * All goroutines you create should terminate before main returns.
    * Applications should be capable of shutting down on demand, even under load, in a controlled way.
        * You want to stop accepting new requests and finish the requests you have (load shedding).
* Identify and monitor critical points of back pressure that can exist inside your application.
    * Channels, mutexes and atomic functions can create back pressure when goroutines are required to wait.
    * A little back pressure is good, it means there is a good balance of concerns.
    * A lot of back pressure is bad, it means things are imbalanced.
    * Back pressure that is imbalanced will cause:
        * Failures inside the software and across the entire platform.
        * Your application to collapse, implode or freeze.
    * Measuring back pressure is a way to measure the health of the application.
* Rate limit to prevent overwhelming back pressure inside your application.
    * Every system has a breaking point, you must know what it is for your application.
    * Applications should reject new requests as early as possible once they are overloaded.
        * Don’t take in more work than you can reasonably work on at a time.
        * Push back when you are at critical mass. Create your own external back pressure.
    * Use an external system for rate limiting when it is reasonable and practical.
* Use timeouts to release the back pressure inside your application.
    * No request or task is allowed to take forever.
    * Identify how long users are willing to wait.
    * Higher-level calls should tell lower-level calls how long they have to run.
    * At the top level, the user should decide how long they are willing to wait.
    * Use the `Context` package.
        * Functions that users wait for should take a `Context`.
            * These functions should select on <-ctx.Done() when they would otherwise block indefinitely.
        * Set a timeout on a `Context` only when you have good reason to expect that a function's execution has a real time limit.
        * Allow the upstream caller to decide when the `Context` should be canceled.
        * Cancel a `Context` whenever the user abandons or explicitly aborts a call.
* Architect applications to:
    * Identify problems when they are happening.
    * Stop the bleeding.
    * Return the system back to a normal state.

---

### Channel Design

Channels allow goroutines to communicate with each other through the use of signaling semantics. Channels accomplish this signaling through the use of sending/receiving data or by identifying state changes on individual channels. Don't architect software with the idea of channels being a queue, focus on signaling and the semantics that simplify the orchestration required.

**Language Mechanics:**

* Use channels to orchestrate and coordinate goroutines.
    * Focus on the signaling semantics and not the sharing of data.
    * Signaling with data or without data.
    * Question their use for synchronizing access to shared state.
        * _There are cases where channels can be simpler for this but initially question._
* Unbuffered channels:
    * Receive happens before the Send.
    * Benefit: 100% guarentee the signal has been received.
    * Cost: Unknown latency on when the signal will be received.
* Buffered channels:
    * Send happens before the Receive.
    * Benefit: Reduce blocking latency between signaling.
    * Cost: No guarentee when the signal has been received.
        * The larger the buffer, the less guarentee.
        * Buffer of 1 can give you one delayed send of guarentee.
* Closing channels:
    * Close happens before the Receive. (like Buffered)
    * Signaling without data.
    * Perfect for signaling cancellations and deadlines.
* NIL channels:
    * Send and Receive block.
    * Turn off signaling
    * Perfect for rate limiting or short term stoppages.

**Design Philosophy:**

Depending on the problem you are solving, you may require different channel semantics. Depending on the semantics you need, different architectural choices must be taken.

* If any given Send on a channel `CAN` cause the sending goroutine to block:
    * Not allowed to use a Buffered channel larger than 1.
        * Buffers larger than 1 must have reason/measurements.
    * Must know what happens when the sending goroutine blocks.
* If any given Send on a channel `WON'T` cause the sending goroutine to block:
    * You have the exact number of buffers for each send.
        * Fan Out pattern
    * You have the buffer measured for max capacity.
        * Drop pattern
* Less is more with buffers.
    * Don’t think about performance when thinking about buffers.
    * Buffers can help to reduce blocking latency between signaling.
        * Reducing blocking latency towards zero does not necessarily mean better throughput.
        * If a buffer of one is giving you good enough throughput then keep it.
        * Question buffers that are larger than one and measure for size.
        * Find the smallest buffer possible that provides good enough throughput.
