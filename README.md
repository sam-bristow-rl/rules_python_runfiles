# `bazel coverage //...` runfiles bug

Trying to run `bazel coverage` in a project with `rules_python` fails when the
`--incompatible_default_to_explicit_init_py` flag is enabled. This doesn't
happen for `bazel test`.

## Works
```
bazel test //...
```

## Works
```
bazel coverage //...
```

## Fails
```
bazel coverage --incompatible_default_to_explicit_init_py //...
```

### Output
```
Executing tests from //:requirements_test
-----------------------------------------------------------------------------
Traceback (most recent call last):
  File "<snip>/execroot/__main__/bazel-out/k8-fastbuild/bin/requirements_test.runfiles/rules_python/python/pip_install/tools/dependency_resolver/dependency_resolver.py", line 26, in <module>
    from python.runfiles import runfiles
ModuleNotFoundError: No module named 'python.runfiles'; 'python' is not a package
```
