# Reactor

https://projectreactor.io/

https://projectreactor.io/docs/core/release/reference/

https://projectreactor.io/docs/core/release/reference/#getting-started-introducing-reactor


https://projectreactor.io/docs/core/release/reference/#intro-reactive

**Reactive programming** is an asynchronous programming paradigm concerned with data streams and the propagation of change. 
This means that it becomes possible to express static (e.g. arrays) or dynamic (e.g. event emitters) data streams with ease via the employed programming language(s).
— https://en.wikipedia.org/wiki/Reactive_programming

**RxJava** implemented reactive programming on the JVM

The **Publisher** notifies the **Subscriber** of newly available values _as they come_, and this push aspect is the key to being reactive. 

In addition to pushing values, the error-handling and completion aspects are also covered in a well defined manner. A Publisher can push new values to its Subscriber (by calling **onNext**) but can also signal an error (by calling **onError**) or completion (by calling **onComplete**).

There are, broadly, two ways one can **improve a program’s performance**:
* **parallelize** to use more threads and more hardware resources.
* **seek more efficiency** in how current resources are used.


Java offers two models of **asynchronous programming**:
* **Callbacks**: Asynchronous methods do not have a return value but take an extra callback parameter (a lambda or anonymous class) that gets called when the result is available. A well known example is Swing’s EventListener hierarchy.
* **Futures**: Asynchronous methods _immediately_ return a Future<T>. The asynchronous process computes a T value, but the Future object wraps access to it. The value is not immediately available, and the object can be polled until the value is available. For instance, an ExecutorService running Callable<T> tasks use Future objects.

Both have drawbacks, described in https://projectreactor.io/docs/core/release/reference/#intro-reactive
  
Reactive libraries, such as Reactor, aim to address these drawbacks of “classic” asynchronous approaches on the JVM while also focusing on a few additional aspects:

* **Composability** and **readability**
* Data as a **flow** manipulated with a rich vocabulary of **operators**
* Nothing happens until you **subscribe**
* **Backpressure** or _the ability for the consumer to signal the producer that the rate of emission is too high_
* **High level** but **high value** abstraction that is _concurrency-agnostic_

By **“composability”**, we mean the ability to orchestrate multiple asynchronous tasks, in which we use results from previous tasks to feed input to subsequent ones. Alternatively, we can run several tasks in a fork-join style. In addition, we can reuse asynchronous tasks as discrete components in a higher-level system.

The ability to orchestrate tasks is tightly coupled to the **readability and maintainability of code**. As the layers of asynchronous processes increase in both number and complexity, being able to compose and read code becomes increasingly difficult. Reactor offers rich composition options, wherein code mirrors the organization of the abstract process, and everything is generally kept at the same level (nesting is minimized).

Each **operator** adds behavior to a Publisher and wraps the previous step’s Publisher into a new instance. The whole chain is thus linked, such that data originates from the first Publisher and moves down the chain, transformed by each link. Eventually, a Subscriber finishes the process. Remember that nothing happens until a Subscriber subscribes to a Publisher.
  
By the act of **subscribing**, you tie the Publisher to a Subscriber, which triggers the flow of data in the whole chain. This is achieved internally by a single request signal from the Subscriber that is propagated upstream, all the way back to the source Publisher.  
  
Propagating signals upstream is also used to implement **backpressure**; a feedback signal sent up the line when a "workstation" processes more slowly than an upstream workstation. A subscriber can work in _unbounded_ mode and let the source push all the data at its fastest achievable rate or it can use the _request mechanism_ to signal the source that it is ready to process at most n elements.
  
The Rx family of reactive libraries distinguishes two broad categories of reactive sequences: **hot** and **cold**. This distinction mainly has to do with how the reactive stream reacts to subscribers:
* A **Cold** sequence starts anew for each Subscriber, including at the source of data. For example, if the source wraps an HTTP call, a new HTTP request is made for each subscription.
* A **Hot** sequence does not start from scratch for each Subscriber. Rather, late subscribers receive signals emitted after they subscribed. 
  
## Patterns

The **observer pattern** is a software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, 
and notifies them automatically of any state changes, usually by calling one of their methods.
— https://en.wikipedia.org/wiki/Observer_pattern

In object-oriented programming, the **iterator pattern** is a design pattern in which an iterator is used to traverse a container and access the container's elements. 
The iterator pattern decouples algorithms from containers; in some cases, algorithms are necessarily container-specific and thus cannot be decoupled.
— https://en.wikipedia.org/wiki/Iterator_pattern
