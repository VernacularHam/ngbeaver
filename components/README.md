# NGBeaver Training Module - Components and Directives

This project is designed to help learn good practices for how to structure components and use directives in Angular.

## What are Components?

Technically, components are a type of 'directive' in Angular, but I prefer to think of them distinctly since they're used so heavily. In effect, a Component is a Typescript class that implements the requirements of the Component interface and has a related HTML template that describes its internal structure and appearance. This is not dissimilar to the concept of a view and acode-behind for those familiar with that from a variety of C# use cases.

Much of the work in designing and building the UI will involve creating and using components - both those stock ones made available through Angular and those made by your peers.

The Angular documentation describing Components is [here](https://angular.io/guide/architecture-components).

For our purposes, we will divide components into further subdivisions:

### Composite Components

Composite components are just what the label on the tin says - composited from other components. They are assembled from a selection of Angular [stock components](https://angular.io/api?type=directive) and components made by us. A composite component can even be assembled from other, simpler composite components.

### Template Components

The concept behind Template components is that they are fundamentally structural - focused on delivering the scaffolding to shape our UI either functionally or visually. They should by their nature be composed only of bog standard HTML - though there may be appropriate cases where a component with a few Angular stock components might also be reasonably called 'template'. The division isn't designed as a straitjacket, but rather as a means to define the expectations of a given component. A button with certain hooks for behaviors on different user interactions might be a template, a series of buttons each tied to calling specific business logic services is a composite.

## What are Directives?

Directives modify existing html rather than providing a <custom-tag></custom-tag> like components do. They come in two varieties - structural and attribute.

### Structural Directives

Easily explained [here](https://angular.io/guide/structural-directives).


### Attribute Directives

Explained [here](https://angular.io/guide/attribute-directives)

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.0.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. Run `ng generate directive directive-name` to generate a directive.
