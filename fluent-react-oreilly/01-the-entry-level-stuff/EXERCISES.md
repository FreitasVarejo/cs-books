# Exercises

1. What was the motivation to create React?
   Answer: the state of the art for JS frameworks (Angular js) had problems with
   escalability (required a complex structure to admit two-way binding using
   directives), agile manipulation of DOM, lack of independent and modular
   components. That ended up with a spagetti code.
   The main motivation was solving the problem of making reliable UI updates at
   scale. React took full control of the interface state to avoid unpredictable
   and error-prone direct DOM manipulations

2. How does React improve on prior patterns like MVC and MVVM?
   Answer: React decoupled even more the `View` from `Controller`/`View-Model`,
   creating a feedback loop (unidirectional data flow) in a way that the output
   of a change in the interface is shown by the `Views` only when it has been
   processed by `Stores`.
   (8/10) => Besides replacing two-way data binding with unidirectional data
   flow, React simplified MVC by treating UI components essentially as
   functions (receiving props as inputs and returning elements as outputs)

3. What’s so special about the Flux architecture?
   Answer: The inovation of unidirectional data flow.
   (9/10) => Stores permited central single source of truth. Also permmited
   testability because of the separation of responsabilities.

4. What are the benefits of declarative programming abstractions?
   Answer: The programmer can only declare the logic of how the interface should
   behave, and the programming language takes care of how it is implemented
   behind the scenes (the book gave me a extremely vague explanation)
   (9/10) => React kept the updates to itself rather than the programmer

5. What’s the role of the virtual DOM in making efficient UI updates?
   Answer By creating sequential snapshots of how the DOM should look like
   (Virtual DOM), the React framework takes care on figuring out the minimal
   effort taken to change the initial Virtual DOM to an later Virtual DOM, then
   the React framework makes analogous changes to the initial DOM to the later
   DOM with also minimal effort.
   (10/10)
