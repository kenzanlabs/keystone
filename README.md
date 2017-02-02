## Keystone

The goal behind this project is to provide developers with the tools they need for easily setting up and configuring
a build system for a Front-End project by reducing boilerplate and providing out of the box functionality for the most
common of use cases.  This will be accomplished by creating a number of Gulp pipelines that can be used individually,
or configured for your project using a Yeoman Generator.

This top level repo acts as an umbrella for general information, common issues, feature  requests, bug reports,
etc about all the related projects.

**Currently this project is in phase 1, and as such only the pipelines are in development.**

## Governance
The governing team will be:
* Paul Barry - @paul-barry-kenzan 
* Owen Buckley - @thescientist13 (Project Lead)
* Rona Kilmer - @rkunboxed 
* Megan Sharon - @mgnsharon 

## Roadmap
The current 2017 Roadmap for the project is

| Milestone     |   Date   | Notes |
| ------------- | -------- | ------ |
| Generator Lifecycle | Q1 | [Milestone 1][] of the Keystone generator project; existing pipeline support and maintenace |
| Generator Lifecycle - Enhancements | TBD | [Milestone 2][] of the Keystone generator project, existing pipeline support and maintenace |

[Milestone 1]: https://github.com/kenzanlabs/generator-keystone/milestones/Sprint%201:%20Generator%20Lifescycle%20(MVP)
[Milestone 2]: https://github.com/kenzanlabs/generator-keystone/milestones/Sprint%202:%20Generator%20Lifecycle%20Enhancements

## Tools
- [Node][] - the development environment
- [Gulp][] - the task runner
- [Yeoman][] - the scaffold generator

[Node]: https://nodejs.org/
[Gulp]: https://www.gulpjs.com/
[Yeoman]: http://yeoman.io/

## Generator
Keystone has reached a point where active development on the [Generator][] can begin.  Two [milestones][] have been defined and are in active development now (see the above Roadmap section).  Please visit the repo to provide feedback and contribute!

[Generator]: https://github.com/kenzanlabs/generator-keystone
[milestones]: https://github.com/kenzanlabs/generator-keystone/milestones

## Pipelines
Pipelines are designed with a stream in / stream out API interface.  The intent is that these pipelines can be used
a la carte any project, and in any combination needed.  Currently, we have

### Component Pipelines
Component pipelines are wrappers around base level gulp plugins for any number of low level build needs.   They
follow a standard naming convention that clearly identifies their function

`pipeline-{component}-{target}`


| Component     |   Role   | Target |
| ------------- | -------- | ------ |
| Archive | Bundling all files into a single file for distribution or backup | .tar, .zip |
| Compile | Compiling from higher level languages to native source | LESS, CoffeeScript, TypeScript |
| Document | Documentation generation | ngDocs, KSS |
| Minify | "Building" of static assets for production or local build environments | minify / concat (JS, CSS, HTML) |
| Template | HTML assembly from partials or auto templating in dependencies | inject, wiredeps, handlebars, mustache |
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
var exampleKeystonePipeline = require('pipeline-example');

gulp.task('some-task', function() {
  return gulp.src(['src/**/*.js'])
    .pipe(exampleKeystonePipeline.runTask({
      optionA: true,
      optionB: false
     }));
    .pipe(otherPlugin());
    .pipe(gulp.dest('dest/');
});
```

### Active Projects
| Package       | Description   | Repo |
| ------------- | ------------- | ---- |
| generator-keystone | Yeoman Generator for scaffolding new builds leveraging Keystone pipelines | https://github.com/kenzanlabs/generator-keystone |
| pipeline-compile-less | Pipeline to compile LESS into CSS | https://github.com/kenzanlabs/pipeline-compile-less |
| pipeline-compile-sass | Pipeline to compile SASS into CSS | https://github.com/kenzanlabs/pipeline-compile-sass |
| pipeline-handyman | Utility pipeline for pipeline repos | https://github.com/kenzanlabs/pipeline-handyman |
| pipeline-minify-css | Pipeline to minify and optionally concat CSS | https://github.com/kenzanlabs/pipeline-minify-css |
| pipeline-minify-js | Pipeline to minify and optionally concat JS | https://github.com/kenzanlabs/pipeline-minify-js |
| pipeline-test-node | Pipeline to test Node packages | https://github.com/kenzanlabs/pipeline-test-node |
| pipeline-validate-css | Pipeline to lint / styleguide check CSS | https://github.com/kenzanlabs/pipeline-validate-css |
| pipeline-validate-js | Pipeline to lint / styleguide check JS / ESLint | https://github.com/kenzanlabs/pipeline-validate-js |
| pipeline-validate-html | Pipeline to lint HTML files via HTMLLint | https://github.com/kenzanlabs/pipeline-validate-html |


## LICENSE
Copyright 2015 Kenzan, LLC <http://kenzan.com>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
