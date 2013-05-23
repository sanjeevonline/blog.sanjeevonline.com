---
template: article.jade
title: Exception handling guidelines/best practices
date: 2010-12-20 15:00
author: sanjeev
aliases: ['/post/2007/01/08/code-and-stuff/', '/post/2007/01/08/first/', '/post/2008/01/08/first']
categories: [technology]
tags: [java, best-practices]
excerpt: Lets review some basic xception design guidelines in Java
---

Let’s review some basic exception design guidelines, summarized from Object Design: Roles, Responsibilities, and Collaborations (Rebecca Wirfs-Brock and Alan McKean, Addison-Wesley, 2003).

* <b>Don’t try to handle coding errors</b>: Unless your software is required to take extraordinary measures in error scenarios, don’t spend a lot of time designing it to detect and recover from programming errors. In the case of an out-of-bounds array index, divide-by zero error, or any other programming error, the best strategy is to fail fast (and leave an audit trail of the problem that can be used to troubleshoot it).
* <b>Avoid declaring lots of exception classes</b>: Create a new exception class only when you expect some handling of the code to take a significantly different action, based on the exception type. In my experience it is rarely the case and exception classes available in java API serve the purpose.

<span class="more"></span>

* <b>Recast lower-level exceptions to higher-level ones whenever you raise an abstraction level</b>: Don’t let implementation details leak out of a method invocation as exceptions. Otherwise, your users might think your software is broken. When low-level exceptions percolate up to a high-level handler, there’s little context to assist the handler in making informed decisions or reporting conditions that are traceable to any obvious cause. Recasting an exception whenever you cross an abstraction boundary enables exception handlers higher up in the call chain to make more informed decisions. If you want to include a problem trace when recasting them, you can always create a chained exception. A chained exception provides added context and holds a reference to the original lower level exception. You can repeatedly chain exceptions.
* <b>Provide context along with an exception</b>: What’s most important in exception handling is information that helps create an informed response. Exception classes hold information. You can design them to be packed with information in addition to the bare-bones stack trace information provided by default. You might include values of parameters that raised the exception, specific error text, or detailed information that could be useful to plan a recovery. When an exception occurs, it is important that all pertinent data be passed to the exception's constructor. Such data is often critical for understanding and solving the problem, and can greatly reduce the time needed to find a solution.
The this reference is sometimes useful for this purpose, since toString is implicitly called. In addition, if you are defining exception classes yourself, you may even design your constructors to force the caller to pass the pertinent data.
	
	Uninformative stack traces are very frustrating for the maintainer, and often inspire even the most well-tempered programmers to temporarily violate local community standards for obscenity.

	Example
	
	```
public final class RangeChecker {

  /**
  * Return <code>true</code> only if <code>aNumber</code> is in the range
  * <code>aLow..aHigh</code> (inclusive).
  *
  * @param <code>aLow</code> less than or equal to <code>aHigh</code>.
  */
  static public boolean isInRange( int aNumber, int aLow, int aHigh ){
    if (aLow > aHigh) {
      throw new IllegalArgumentException("Low:" + aLow + " greater than High:" + aHigh);
    }
    return (aLow <= aNumber && aNumber <= aHigh);
  }
}
```

* <b>Handle exceptions as close to the problem as you can</b>: As a first line of defense, consider the initial requestor. If the caller knows enough to perform a corrective action, you can rectify the condition on the spot. If you propagate an exception far away from the source, it can be difficult to trace the source. Often objects further away from the problem can’t make meaningful decisions.
* <b>Use exceptions only to signal emergencies</b>: Exceptions shouldn’t be raised to indicate normal branching conditions that will alter the flow in the calling code. For example, a find operation may return zero, one, or many objects, so I wouldn’t raise an exception in this case. Instead, I’d design my find() method to return a null object or an empty collection. A dropped database connection, on the other hand, is a real emergency. There’s nothing that can be done to continue as planned.
* <b>Don’t repeatedly re-throw the same exception</b>: Although exceptions don’t cost anything until they’re raised, programs that frequently raise exceptions run more slowly.
* <b>Avoid empty catch blocks</b>: It is usually a very bad idea to have an empty catch block because when the exception occurs, nothing happens, and the program fails for unknown reasons.

	In general, when a exception occurs, it can be thrown up to the caller, or it can be caught in a catch block. When catching an exception, some options include :

 		** Inform the user (strongly recommended)
 		** Log the problem, using the application specific loggers or JDK logging services, or similar tool
 		** Send an email describing the problem to an administrator
 		
	Deciding what exactly to do seems to depend on the nature of the problem. If there is an actual bug in the program - a defect that needs to be fixed - then one might do all three of the above. In this case, the end user should likely be shown a generic "Sorry, we goofed" message, not a stack trace. It is usually considered bad form to display a stack trace to a non-technical end user, or if exposing a stack trace may be a security risk.

	If the exception does not represent a bug, then different behavior may be appropriate. For example, if a problem with user input is detected and an exception is thrown as a result, then merely informing the user of the problem might be all that is required.
* <b>Exception translation</b>: Occasionally, it is appropriate to translate one type of exception into another.

	The data layer, for example, can profit from this technique. Here, the data layer seeks to hide almost all of its implementation details from other parts of the program. It even seeks to hide the basic persistence mechanism - whether or not a database or an ad hoc file scheme is used, for example.

	However, every persistence style has specific exceptions - SQLException for databases,  and IOException for files, for example. If the rest of the program is to remain truly ignorant of the persistence mechanism, then these exceptions cannot be allowed to propagate outside the data layer, and must be translated into some higher level abstraction - DataAccessException, say.
* <b>Use template for repeated try-catch</b>: Java's try-catch blocks are particularly common when using APIs which give an important role to checked exceptions (such as SQLException in JDBC). When using such an API, many published examples simply repeat the same try-catch code structure whenever necessary. However, it is simple to eliminate such code repetition using the template method pattern. The idea is to define the structure of the try-catch block in one place, in an abstract base class (ABC). Such an ABC is then extended whenever that particular try-catch block is needed. The concrete implementation of such an ABC will often have simple, "straight line" code.
