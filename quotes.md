> A monorepo helps reduce the cost of software development. It does this in three different ways: by being simpler to use, by providing better discoverability, and by allowing atomicity of updates.

Поведение полирепозитория по умолчанию – изоляция.

Поведение монорепозитория по умолчанию – совместная ответственность и видимость.

Keep in mind monolithic source control does not necessarily result in monolithic software. And microservices can play well with monorepo

There are two basic types of Monorepos are huge repositories containing all the code maintained by a company or project specific Monorepos like Babel, React

__monorepo !== monolith__. Quite the contrary, because monorepos simplify code sharing and cross-project refactorings, they significantly lower the cost of creating libs, microservices and microfrontends. So adopting a monorepo often enables more deployment flexibility.

Monorepo-style development is a software development approach where:
- You develop multiple projects in the same repository.
- The projects can depend on each other, so they can share code.
- When you make a change, you do not rebuild or retest every project in the monorepo. Instead, you only rebuild and retest the projects that can be affected by your change.

## What is an monorepo?
The repository contains more than one logical project (e.g. an iOS client and a web-application). These projects are most likely unrelated, loosely connected or can be connected by other means (e.g via dependency management tools)
The repository is large in many ways: Number of commits, Number of branches and/or tags, Number of files tracked, Size of content tracked (as measured by looking at the .git directory of the repository)
### Advantages
- Unified versioning, one source of truth;
- Extensive code sharing and reuse;
- Simplified dependency management;
- Atomic changes;
- Large-scale refactoring;
- Collaboration across teams;
- Flexible team boundaries and code ownership; and
- Code visibility and clear tree structure providing implicit team namespacing.

#### Simplified organization
With multiple repos, you typically either have one project per repo, or an umbrella of related projects per repo, but that forces you to define what a “project” is for your particular team or company, and it sometimes forces you to split and merge repos for reasons that are pure overhead. For example, having to split a project because it's too big or has too much history for your VCS is not optimal.

With a monorepo, projects can be organized and grouped together in whatever way you find to be most logically consistent, and not just because your version control system forces you to organize things in a particular way. Using a single repo also reduces overhead from managing dependencies.

A side effect of the simplified organization is that it's easier to navigate projects. The monorepos I've used let you essentially navigate as if everything is on a networked file system, re-using the idiom that's used to navigate within projects. Multi repo setups usually have two separate levels of navigation -- the filesystem idiom that's used inside projects, and then a meta-level for navigating between projects.

A side effect of that side effect is that, with monorepos, it's often the case that it's very easy to get a dev environment set up to run builds and tests. If you expect to be able to navigate between projects with the equivalent of cd, you also expect to be able to do cd; make. Since it seems weird for that to not work, it usually works, and whatever tooling effort is necessary to make it work gets done1. While it's technically possible to get that kind of ease in multiple repos, it's not as natural, which means that the necessary work isn't done as often.

#### Simplified dependencies
This probably goes without saying, but with multiple repos, you need to have some way of specifying and versioning dependencies between them. That sounds like it ought to be straightforward, but in practice, most solutions are cumbersome and involve a lot of overhead.

With a monorepo, it's easy to have one universal version number for all projects. Since atomic cross-project commits are possible, the repository can always be in a consistent state -- at commit #X, all project builds should work. Dependencies still need to be specified in the build system, but whether that's a make Makefiles or bazel BUILD files, those can be checked into version control like everything else. And since there's just one version number, the Makefiles or BUILD files or whatever you choose don't need to specify version numbers.

#### Tooling
The simplification of navigation and dependencies makes it much easier to write tools. Instead of having tools that must understand relationships between repositories, as well as the nature of files within repositories, tools basically just need to be able to read files (including some file format that specifies dependencies between units within the repo).

### Costs and trade-offs
- Tooling investments for both development and execution;
- Codebase complexity, including unnecessary dependencies and difficulties with code discovery; and
- Effort invested in code health.

## Lerna based monorepos
- babel : compiler for writing next generation JavaScript
- create-react-app : create React apps with no build configuration
- react-router : Declarative routing for React
- jest : Delightful JavaScript Testing
- storybook : Interactive UI component dev & test
