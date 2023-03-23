# rules_python regression with url dependencies

To reproduce:

```sh
bazel query @pip_pyyaml//...
```

This worked with rules_python 0.16.1, doesn't work with 0.20.0.
