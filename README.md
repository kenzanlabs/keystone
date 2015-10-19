## Keystone

The goal behind this project is to provide developers with the tools they need for easily setting up and configuring
a build system for a Front-End project by reducing boilerplate and providing out of the box functionality for the most
common of use cases.  This will be accomplished by creating a number of Gulp pipelines that can be used individually,
or configured for your project using a Yeoman Generator.  This top level project sets the expectations and goals, as
well as overview for the project and how to get started.

## Status
Currently this project is in phase 1, and as such only the pipelines are in development.  Generator development TBD.

## Tools
- [Node][] - the development environment
- [Gulp][] - the task runner
- [Yeoman][] - the scaffold generator

[Node]: https://nodejs.org/
[Gulp]: https://www.gulpjs.com/
[Yeoman]: http://yeoman.io/

## Generator
TBD


## Pipelines
Pipelines are designed with a stream in / stream out API interface.  The intent is that these pipelines can be used
a la carte any project, and in any combination needed.  Currently, we have

### Component Pipelines
Component pipelines are wrappers around base level gulp pipelines for any number of low level build needs.   They
follow a standard naming convention that clearly identifies their function

`pipeline-{component}-{target}`


| Component     |   Role   | Target |
| ------------- | -------- | ------ |
| Archive | Bundling all files into a single file for distribution or backup | .tar, .zip |
| Compile | Compiling from higher level languages to native source | LESS, CoffeeScript, TypeScript |
| Document | Documentation generation | ngDocs, KSS |
| Minify | "Building" of static assets for production or local build environments | minify / concat (JS, CSS, HTML) |
| Temoplate | HTML assembly from partials or auto templating in dependencies | inject, wiredeps, handlebars, mustache |
| Test | Unit and e2e testing | node, karma, protractor |
| Validate | Linting and styleguide checking | jscs, jslint, html-lint, css lint, less lint |

### Feature Pipelines
TBD

### Usage
Pipelines should expect a stream and return a stream (SISO).  This allows using Keystone pipelines easily with other
pipelines

```javascript
var gulp = require('gulp');
var otherPlugin = require('other-plugin');
var exampleKeystonePipeline = require('pipeline-example')({
  optionA: true,
  optionB: false
});

gulp.task('some-task', function() {
  return gulp.src(['src/**/*.js'])
    .pipe(exampleKeystonePipeline.runTask());
    .pipe(otherPlugin());
    .pipe(gulp.dest('dest/');
});
```

### Active Projects
| Package       | Description   | Repo |
| ------------- | ------------- | ---- |
| pipeline-compile-less | Pipeline to compile LESS into CSS | https://github.com/kenzanmedia/pipeline-compile-less |
| pipeline-handyman | Utility pipeline for pipeline repos | https://github.com/kenzanmedia/pipeline-handyman |
| pipeline-minify-css | Pipeline to minify and optionally concat CSS | https://github.com/kenzanmedia/pipeline-minify-css |
| pipeline-minify-js | Pipeline to minify and optionally concat JS | https://github.com/kenzanmedia/pipeline-minify-js |
| pipeline-test-node | Pipeline to test Node packages | https://github.com/kenzanmedia/pipeline-test-node |
| pipeline-validate-css | Pipeline to lint / styleguide check CSS | https://github.com/kenzanmedia/pipeline-validate-css |
| pipeline-validate-js | Pipeline to lint / styleguide check JS / ESLint | https://github.com/kenzanmedia/pipeline-validate-js |

