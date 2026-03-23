**debouncing:** technique that avoids race condition by allowing the execution of a function only after a certain time passed since the last execution of the same function

**throttling:** technique that avoids race condition by prohibiting two or more execution of a function per arbitrary time section (ex: one time per minute, one time per hour)

**DOM Documento Object Model):** it is equivalent for the AST decomposition for the c, but for the HTTP in frontend development. it is the product of the decomposition of the HTML file into a tree of components by the browser. Besides it can also react dinamically to changes after being parsed.

## Frameworks before React

**MVC Pattern:** applied in Backbone framework

1. `Model`: Contains business logic and data memory, isolating them from the UI (`View`).
2. `View`: UI of the application. Displays data from `Model` and send commands to `Controller`.
3. `Controller`: takes inputs from `View`, process, updates `Model` and only then the output is sent to `View`.
   \*\* Pros:


    * Decouples business logic, user interface and user inputs in the code.

\*_ Cons:
_ Controllers can conflict with other controllers responsibilities and states as code scales up.
_ Two-way data binding: cretates inconsistencies between `View` and `Model` states.
_ Sections endup tightly coupled as code scales up.

**MVVM Pattern:** applied in Knockout framework

1. `Model`: Contains business logic and data memory, isolating them from `View` AND `View-Model`.
2. `View`: UI of the application. Reflect changes directly from `View-Model`.
3. `View-Model`: Exposes data and commands to `View`. Changes between them are reflected automatically.
   \*\* Pros:


    * Introduction of `View-Model` brougth way less states conflicts compared to `Crontrolers`.
    * You could test the `View-Model` separated from the `View`.

**Angular JS:** introduced dependency injection

- Binded `View` to `Model` using HTML directives (`Two-way binding`).

## Enter React (TODO)

## Exercises

1.  What was the motivation to create React?
    Answer: the state of the art for JS frameworks (Angular js) had problems with escalability (required a complex structure to admit two-way binding using directives), agile manipulation of DOM, lack of independent and modular components. That ended up with a spagetti code.
    The main motivation was solving the problem of making reliable UI updates at scale. React took full control of the interface state to avoid unpredictable and error-prone direct DOM manipulations

2.  How does React improve on prior patterns like MVC and MVVM?
    Answer: React decoupled even more the `View` from `Controller`/`View-Model`, creating a feedback loop (unidirectional data flow) in a way that the output of a change in the interface is shown by the `Views` only when it has been processed by `Stores`.
    (8/10) => Besides replacing two-way data binding with unidirectional data flow
    , React simplified MVC by treating UI components essentially as functions (receiving props as inputs and returning elements as outputs)

3.  What’s so special about the Flux architecture?
    Answer: The inovation of unidirectional data flow.
    (9/10) => Stores permited central single source of truth. Also permmited testability because of the separation of responsabilities.

4.  What are the benefits of declarative programming abstractions?
    Answer: The programmer can only declare the logic of how the interface should behave, and the programming language takes care of how it is implemented behind the scenes (the book gave me a extremely vague explanation)
    (9/10) => React kept the updates to itself rather than the programmer

5.  What’s the role of the virtual DOM in making efficient UI updates?
    Answer By creating sequential snapshots of how the DOM should look like (Virtual DOM), the React framework takes care on figuring out the minimal effort taken to change the initial Virtual DOM to an later Virtual DOM, then the React framework makes analogous changes to the initial DOM to the later DOM with also minimal effort.
    (10/10)
