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
