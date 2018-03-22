# Code Loading

When a Julia program does `import X` or `using X` the identity and location of the package `X` is resolved in terms of the `LOAD_PATH` and `DEPOT_PATH` global variables. Julia packages are identified by UUID – "[Universally unique identifier](https://en.wikipedia.org/wiki/Universally_unique_identifier)" – assigned to each package when it is created. This UUID identifies the package premanently, even if it is renamed, its repository location, changed, it changes of ownership/maintainership, or someone forks is (unless they fork it with the intention of creating a *new* separate package, in which case they must change the UUID). UUIDs provide a simple answer to the question of whether two Julia source trees are "the same package": if they have the same UUID in their project files, then they are the same package, otherwise they are not.

!!! note
	Julia package UUIDs serve a similar purpose to Java's reversed domain package names. For example, in Java you might see `import com.sun.net.httpserver.HttpServer;` which imports the `HttpServer` class from the `com.sun.net.httpserver`. This package name suggests that the `httpserver` package is maintained by Sun Microsystems, the former owner of `sun.com`. Of course, Sun Microsystems no longer exists, having been acquired by Orcale in 2010. The `com.sun` packages are permanent, however, and even if Oracle hit rough times and decided to auction off its `sun.com` domain, all Java code everywhere would continue to include this no-longer relevant domain. Since UUIDs lack have no meaning, they don't have this problem. On the flip side, they are very hard for humans to remember ot types. Fortnately, Julia's [package manager](https://julialang.org/Pkg3.jl/latest/) keeps UUIDs mostly out of sight and they never appear in your Julia code.

for example, but since UUIDs have no meaning, they can handle package renames and even changing the controlling entitity of a package. In the case, for example, Sun Microsystems no longer exists, and `sun.com` redirects to `oracle.com`. 



The load path is a stack of "environments", each of which provides three things:

1. `roots`: a map from top-level names to UUIDs
2. `graph`: a graph of dependencies from 

searched for in the load path, which is controlled by the `LOAD_PATH` global array 