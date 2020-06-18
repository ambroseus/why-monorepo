## wiki

In revision control systems, a monorepo ("mono" from Greek μόνος, mónos, 'single, alone' and "repo" short for repository) is a software development strategy where code for many projects is stored in the same repository. some forms of this software engineering practice were over a decade old, but the general concept had only recently been named. Many attempts have been made to differentiate between monolithic applications and other, newer forms of monorepos. 

Google, Facebook, Microsoft, Uber, Airbnb and Twitter all employ very large monorepos with varying strategies to scale build systems and version control software with a large volume of code and daily changes.

### Advantages

There are a number of potential advantages to a monorepo over individual repositories:

- Ease of code reuse – Similar functionality or communication protocols can be abstracted into shared libraries and directly included by projects, without the need of a dependency package manager.
- Simplified dependency management – In a multiple repository environment where multiple projects depend on a third-party dependency, that dependency might be downloaded or built multiple times. In a monorepo the build can be easily optimized, as referenced dependencies all exist in the same codebase.
- Atomic commits – When projects that work together are contained in separate repositories, releases need to sync which versions of one project work with the other. And in large enough projects, managing compatible versions between dependencies can become dependency hell.[8] In a monorepo this problem can be negated, since developers may change multiple projects atomically.
- Large-scale code refactoring – Since developers have access to the entire project, refactors can ensure that every piece of the project continues to function after a refactor.
- Collaboration across teams – In a monorepo that uses source dependencies (dependencies that are compiled from source), teams can improve projects being worked on by other teams. This leads to flexible code ownership.

### Limitations and disadvantages

- Loss of version information – Although not required, some monorepo builds use one version number across all projects in the repository. This leads to a loss of per-project semantic versioning.
- Lack of per-project security – With split repositories, access to a repository can be granted based upon need. A monorepo allows read access to all software in the project, possibly presenting new security issues.
- More storage needed – With split repositories, you can fetch only the project you are interested in. With a monorepo, you might need to fetch all projects. Note that this depends on the versioning system. This is not an issue if you use e.g. SVN in which you can download any part of the repo (even a single directory).
