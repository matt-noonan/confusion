# confusion

This repo, along with https://github.com/matt-noonan/fake-array-test, demonstrate a mild depedency confusion issue with `stack`.

```
$ stack --version # on OS X 10.15.7
Version 2.5.1, Git revision d6ab861544918185236cf826cb2028abb266d6d5 x86_64 hpack-0.33.0
```

The project has a dependency on `array`, but the `stack.yaml` file has an `extra-dep` that points to a git repo with
a *different* package, also called `array`.

If the package in that repo has a version *different* from 0.5.4.0, then the repo's package is used.
If the package in that repo has a version *equal* to 0.5.4.0, then it appears that `array` from the LTS is used.

Note that 0.5.4.0 is the version of `array` contained in LTS 17.2

The repo has several different versions committed, all with identical code. You can easily switch between versions
by uncommenting the corresponding commit in the `stack.yaml` file.
