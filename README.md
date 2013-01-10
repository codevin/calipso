
This is branch off  [calipso](https://github.com/cliftonc/calipso)'s master.

The idea of appModule is that you can create applications easily on top of calipso as application base since calipso provides a variety of built-in capabilities which it uses for the CMS functionality.

Unlike simple examples, one can start off a major application project this way, leveraging the capabilities already contributed, integrated and tested in calipso. These capabilities include:
* User login with support for facebook, google single signs.
* themes support
* Internal modules which are properly booted and configured, and can be dynamically brought down and up.
* An admin area (which leverages CMS capabilities) that can be used for managing, reporting etc.
* Clustering support


To start off a new project, user downloads a sample project which includes a **package.json** file which in turn includes this calipso build as a dependency. 

A sample app which leverages this approach is in the works. Currently one can play with [todoApp](https://github.com/codevin/todoApp), which can be installed as a module within a standard calipso deployment. 

Changes being done to calipso to support this functionality:

1. PrivateThemes support, so modules can have their own themes, public files etc. This has already been done and checked in by Andreas (richtera). 
2. Cleanup include dependencies for lib/calipso in various files within calipso.
3. lib/core/Module.js, which loads a module, now supports loading modules listed by name and path individually, 
   apart from the base path. 

Additional changes being done in the sample application (todoApp) as additional framework code, which will be integrated into calipso:
1. Simpler app code, focusing on your app, and minimizing the dependency on calipso.
2. App will register a '/app' as the owner of the URL space, and then do its own URL management within the app itself (currently using flatiron/director module). 
3. Much simpler approach to using blocks within the themes UI. For e.g. support for __'render(template, results, 'section')__ to push something into a template.
4. Support for partials (in EJS templates), so you can build complex applications.
5. And more functionalities (independent of calipso), helping one to get application up and running fast.

TODO:
1. Segregate existing calipso modules into different groups:
   * Capability providers: E.g. User, Mailing 
   * Applications: Content, Admin - which are their own applications.
   * Some modules which are actually part of the applications, for e.g. content Versioning capability.

2. Change the way the modules register then paths, so the app modules "own" the paths. Other modules 
   introduce their blocks only if they have been requested by application modules.

 


