Minimal reproduction for bazelbuild/rules_go#3154

```
$ git checkout main
Already on 'main'
Your branch is up to date with 'origin/main'.
$ bazel build //:rules_go-3154-repro
INFO: Analyzed target //:rules_go-3154-repro (20 packages loaded, 7961 targets configured).
INFO: Found 1 target...
Target //:rules_go-3154-repro up-to-date:
  bazel-bin/rules_go-3154-repro_/rules_go-3154-repro
INFO: Elapsed time: 25.030s, Critical Path: 0.01s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action
$ git checkout rules_go_v0-32-0
Switched to branch 'rules_go_v0-32-0'
Your branch is up to date with 'origin/rules_go_v0-32-0'.
$ bazel build //:rules_go-3154-repro
ERROR: /Users/ngooding/Code/rules_go-3154-repro/BUILD.bazel:9:11: no such target '@com_github_golang_mock//gomock:go_default_library': target 'go_default_library' not declared in package 'gomock' defined by /private/var/tmp/_bazel_ngooding/c8197249830d67c697ef8008effff759/external/com_github_golang_mock/gomock/BUILD.bazel and referenced by '//:go_default_library'
ERROR: Analysis of target '//:rules_go-3154-repro' failed; build aborted:
INFO: Elapsed time: 33.532s
INFO: 0 processes.
FAILED: Build did NOT complete successfully (14 packages loaded, 7752 targets configured)
```
