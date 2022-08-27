---
title: Migrating from version 2
menu: Migration from version 2
template: jaxon
---

### New Features
Many parts of the library have been rewritten, many classes have been moved and renamed, for more simplicity, readability and performance.

- The DI container has been greatly improved, and is now widely used across the library. For example, there’s no more calls to the global `jaxon()` function in the library.

- Interfaces have been defined for request and response plugins, making it easier to understand their features.

- New exception classes are added.

- The event dispatcher is removed.

- Some utility features (translator, templates, config, etc) are moved to the new jaxon-utils package.

- There are improvements on the request and response plugin system,the request factory, the upload handler, and the code generator.

The next upcoming feature is annotation. It will allow the developer to define properties of the exported classes together with the classes, using the PHP annotation syntax.
Annotations will be defined for all the options of class registration, and maybe also for validation. One feature that has just been added to this library is the PSR7 and PSR15 support.
Jaxon is now able to handle input HTTP requests and return HTTP responses as defined by the PSR7 message interfaces. It also provides PSR15 middlewares and request handlers, making it easy to integrate with PHP frameworks or CMSs that support these standards.

### Breaking changes
Some breaking changes have been made

1. Instantiating the Response class will not work anymore, since its constructor now takes
parameters. The Jaxon class must be used to create response objects.

Before

After

It is still recommended to use the global response object.

2. The request and response plugins must now be registered by class name, and not by
instance.

Before

After

By default, the plugin instance will be created using the `auto()` method of the Jaxon DI,
allowing the constructor to take any object registered in the DI as parameter. Optionally,
the DI can be explicitely set for the plugin class, before the registration.

3. The integration plugins
The interface for integration plugin is now simpler. The `processRequest()` method is
removed from the Jaxon App AppTrait trait, and many other methods are added to
define views, session manager, logger and container, makig it easier to define new plugins.