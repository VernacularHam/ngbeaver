# Redux and Angular - NGXS

Redux is a pattern for managing the state of a web-based UI that was first pioneered for use with the ReactJS framework. It is an evolution of the older pattern called Flux. As such, it is easy to end up confused when researching Redux, since the bulk of content related to it speaks explicitly to using it with ReactJS. Furthermore, some patterns of what might be called 'pure' Redux are problematic in Angular.

Redux is about handling communication of data between components using an immutable global state object. In Angular, communication between peer components (i.e. parents and their children) are best handled using the @Input and @Output decorators available through Angular - but Redux becomes relevant when you need to pass information of some kind through components that do not immediately need to use it (Components needing to send data through a parent to reach 'sibling' components, or having to reach grandchildren/grandparent components etc). In pure Angular, this can become highly problematic very quickly as components get burdened passing around loads of data they have no interest in, shoveling it up and down brittle chains of communication that one bad change could easily cripple.

Redux solves this by creating a global state object that can be modified from anywhere in the application, and subscribed to from anywhere in the application. The behavior loop is relatively simple - the global state is called a 'store', and components can leverage 'actions' - predefined functions that modify parts of the global state in specific, predictable ways - to submit changes to the store. Then, components can subscribe to specific parts of the store they are interested in monitoring via 'reducers' that will trigger whenever that portion of the store changes. This allows the sharing and maintenance of complex data objects across diverse areas of the UI in a way that is immediate and responsive.

There are several libraries that have been implemented to bring Redux to Angular, but we've decided to use NGXS, which is itself actually a suite of functions and tools wrapped around the older NGRX library. The [documentation for NGXS](https://ngxs.gitbook.io/ngxs/getting-started) is a great place to start.


## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.
