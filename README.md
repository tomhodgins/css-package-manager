# CSS Package Manager

A plan for a package manager for CSS dependencies and libraries.

## What is it?

This is a repository for brainstorming the requirements and look and feel of a package manager for CSS. You can think of it as something like npm, but for CSS packages instead of JavaScript.

## Why does CSS need a package manager?

Presently CSS authors use a number of different tools:

- preprocessors for extending the ways styles can be expressed and converted to CSS
- libraries frameworks for providing ready-made solutions to common needs
- Houdini worklets providing Layout, Paint, or Animation API features
- Custom property definitions
- (expected: custom at-rule definitions)
- (expected: custom function definitions)
- (expected: custom selector definitions)
- (possible: custom unit definitions)
- minifiers for removing unecessary code from the CSS
- bundlers for packaging CSS and its dependencies together

Also there are other tools, like the CSS-in-JS ecosystem, where style information is embedded inside other languages, workflows, or frameworks.

But there's no coordinated place where your entire CSS workflow can be described, all of its dependencies listed in a way that can be reasoned about, or instructions for how your styles should be packaged and delivered with all their dependencies.

## What would it do?

A package manager for CSS would let authors:

- describe their styling workflow as a process
- define all dependencies used in their project, and their configuration
- automatically fetch and manage dependencies (and dependencies of those dependencies…)
- package the resulting style code in the most efficient formats for delivery (output can include CSS and/or JS, plus other assets like SVG, fonts, etc)

> Imagine a scenario in which one person, let's name this person Cas, loves making Layout API worklets for different tiled layouts. Imagine Cas has made hexagonal layouts, triangular layouts, pentagonal layouts, etc and publishes these Layout API worklets for others to use.
> 
> Next imagine a game designer named Steve finds Cas's tiled layout worklets and thinks they'd be the perfect way to design and build game boards of various sizes and shapes for in-browser games. So Steve publishes a package that consume's Cas's tiled layout worklets and provides a 'game board builder' interface that has  a few easy configurations.
>
> Now you come along, you want to recreate a specific board game experience in the browser that uses a triangular tiled board. Imagine if in your stylesheet all you had to define was this:
>
> ```
> main {
>   display: layout(game-board);
>   --shape: triangle;
>   --size: 100;
> }
> ```
> And once you ran that through a tool, it fetches both Steve's `game-board` package, which itself also requires Cas's triangular tile layout.
>
> To take things one step further, even if Steve's `game-board` layout supports triangular, hexagonal, and pentagonal tiled layouts, since _only_ the triangular mode was used it only bundles that code, leaving the code for supporting hexagonal layouts or pentagonal layouts out of your final build.

## What would it look like?

That's a great question - currently there are many different ideas of how this could be exposed in valid CSS syntax inside CSS stylesheets. Any of the following might be ways this could work:

- a `package.css` file to define folder-wide or project-wide how style information in that folder or project should be

- custom at-rules in CSS that provide a declarative way to describe importing and configuring external dependencies used in that stylesheet

- **can you think of other ways?** open an issue to discuss!

## How does it work?

That part I'm not sure about - I've never built a package manager before, but thankfully many already exist that can be learned from both in what to do and what not to do. Here are two that we can probably learn from as the flesh this one out:

- [gnu guix](http://guix.gnu.org/)
- [npm](https://www.npmjs.com/)

## How can I help?

Open an issue to discuss any idea related to this!