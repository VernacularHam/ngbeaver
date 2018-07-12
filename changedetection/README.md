# NGBeaver Training Module - Performance Considerations and Change Detection in Angular

Let's kick this off with two good articles about Change Detection in Angular that everyone needs to read - both from the excellent [Netanel Basal](https://netbasal.com):

* [Escape from Change Detection](https://netbasal.com/angular-2-escape-from-change-detection-317b3b44906b) (An older article but still relevant)
* [Comprehensive Guide to Angular onPush](https://netbasal.com/a-comprehensive-guide-to-angular-onpush-change-detection-strategy-5bac493074a4)(More recent)

In short, Change Detection is part of Angular's secret sauce powering databinding. Databinding is a fancy name for linking ui event architectures to variables/models storing data, and allowing user initiated behavior (typing, clicking a button) to update a variable in your code immediately, and inversely for that variable to be able to update elements visible to the user. Databinding is one of the key reasons why Javascript frameworks exist, it makes building any kind of interface much easier. Angular achieves databinding by default by leveraging a trick of javascript called 'monkey-patching' to attach hidden event listeners and emitters to your objects and variables. In this way the Angular code running behind your application monitors any and all visual elements and variables for changes, and immediately rebuilds the UI in reaction. There is an enormous amount of optimization built atop that basic concept, but in the end that is what is happening.

This is a problem for large applications. Small applications comprised of a relatively shallow tree of components can leverage default change detection to make implementation quick and easy - but the fact is when default change detection is enabled at every layer of a large app, things get crazy. Essentially, a change at a higher level of the application will cause Angular to re-scan and re-draw every subsidiary component of the one where the change was detected - even if you as a developer are absolutely sure that 90% of those components _have not changed_!

The OnPush strategy informs Angular's ChangeDetection engine to ignore the given component, and not monkeypatch in its listener/emitter architecture to those components. However, the result of this is that knowing when to update elements or in rare cases force the ChangeDetection engine to execute in its entirety are entirely dependent on the developer of the component.

# Browser Performance

It is easy to miss performance issues when testing only in Chrome. Chrome is aggressively designed to maximize website performance, and takes many shortcuts and tricks to reach this goal. Furthermore Angular is developed by Google, and it is safe to assume it is optimized for performance in Chrome. Periodic pauses, slowdowns, and hiccups of an application in Chrome can be _crippling_ performance issues in Edge, Internet Explorer and even Firefox.

_Don't get stuck testing performance only in Chrome!_

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.
