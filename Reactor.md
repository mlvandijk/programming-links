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

## Patterns

The **observer pattern** is a software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, 
and notifies them automatically of any state changes, usually by calling one of their methods.
— https://en.wikipedia.org/wiki/Observer_pattern

In object-oriented programming, the **iterator pattern** is a design pattern in which an iterator is used to traverse a container and access the container's elements. 
The iterator pattern decouples algorithms from containers; in some cases, algorithms are necessarily container-specific and thus cannot be decoupled.
— https://en.wikipedia.org/wiki/Iterator_pattern
