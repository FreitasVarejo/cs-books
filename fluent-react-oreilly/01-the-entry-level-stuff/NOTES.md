# Front-end Optimization and Architectural Patterns

**debouncing:** technique that avoids race condition by allowing the execution
of a function only after a certain time passed since the last execution of the
same function

**throttling:** technique that avoids race condition by prohibiting two or more
execution of a function per arbitrary time section (ex: one time per minute, one
time per hour)

**DOM Documento Object Model):** it is equivalent for the AST decomposition for
the c, but for the HTTP in frontend development. it is the product of the
decomposition of the HTML file into a tree of components by the browser. Besides
it can also react dinamically to changes after being parsed.

## Frameworks before React

**MVC Pattern:** applied in Backbone framework

1. `Model`: Contains business logic and data memory, isolating them from the UI
   (`View`).
2. `View`: UI of the application. Displays data from `Model` and send commands
   to `Controller`.
3. `Controller`: takes inputs from `View`, process, updates `Model` and only
   then the output is sent to `View`.
   \*\* Pros:
   - Decouples business logic, user interface and user inputs in the code.
     \*\* Cons:
   - Controllers can conflict with other controllers responsibilities and
     states as code scales up.
   - Two-way data binding: cretates inconsistencies between `View` and `Model`
     states.
   - Sections endup tightly coupled as code scales up.

**MVVM Pattern:** applied in Knockout framework

1. `Model`: Contains business logic and data memory, isolating them from `View`
   AND `View-Model`.
2. `View`: UI of the application. Reflect changes directly from `View-Model`.
3. `View-Model`: Exposes data and commands to `View`. Changes between them are
   reflected automatically.
   \*\* Pros:
   - Introduction of `View-Model` brougth way less states conflicts compared to
     `Crontrolers`.
   - You could test the `View-Model` separated from the `View`.

**Angular JS:** introduced dependency injection

- Binded `View` to `Model` using HTML directives (`Two-way binding`).

## Enter React (TODO)
