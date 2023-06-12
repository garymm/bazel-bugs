```sh
bazel query @llvm_sycl_toolchain//...
```

Crashes on bazel 6.2.1 with:
```
checking cached actions
    Fetching repository @bazel_toolchain; starting
    Fetching https://github.com/grailbio/bazel-toolchain/archive/c65ef7a45907016a754e5bf5bfabac76eb702fd3.tar.gz
FATAL: bazel crashed due to an internal error. Printing stack trace:
java.lang.RuntimeException: Unrecoverable error while evaluating node '[/Users/garymm/src/garymm/bazel-bugs/llvm-toolchain-starlark]/[WORKSPACE.bazel], 2' (requested by nodes 'com.google.devtools.build.lib.skyframe.ExternalPackageFunction$$Lambda$234/0x00000008002ac840@4bd81363')
	at com.google.devtools.build.skyframe.AbstractParallelEvaluator$Evaluate.run(AbstractParallelEvaluator.java:642)
	at com.google.devtools.build.lib.concurrent.AbstractQueueVisitor$WrappedRunnable.run(AbstractQueueVisitor.java:382)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(Unknown Source)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(Unknown Source)
	at java.base/java.lang.Thread.run(Unknown Source)
Caused by: net.starlark.java.eval.Starlark$UncheckedEvalException: NullPointerException thrown during Starlark evaluation (WORKSPACE)
	at <starlark>.repository_rule(<builtin>:0)
	at <starlark>.<toplevel>(/Users/garymm/src/garymm/bazel-bugs/llvm-toolchain-starlark/WORKSPACE.bazel:17)
Caused by: java.lang.NullPointerException
	at com.google.devtools.build.lib.cmdline.RepositoryName.create(RepositoryName.java:71)
	at com.google.devtools.build.lib.packages.WorkspaceFactoryHelper.addMainRepoEntry(WorkspaceFactoryHelper.java:106)
	at com.google.devtools.build.lib.bazel.repository.starlark.StarlarkRepositoryModule$RepositoryRuleFunction.createRuleLegacy(StarlarkRepositoryModule.java:228)
	at com.google.devtools.build.lib.bazel.repository.starlark.StarlarkRepositoryModule$RepositoryRuleFunction.call(StarlarkRepositoryModule.java:185)
	at net.starlark.java.eval.StarlarkCallable.fastcall(StarlarkCallable.java:86)
	at net.starlark.java.eval.Starlark.fastcall(Starlark.java:638)
	at net.starlark.java.eval.Eval.evalCall(Eval.java:682)
	at net.starlark.java.eval.Eval.eval(Eval.java:497)
	at net.starlark.java.eval.Eval.exec(Eval.java:271)
	at net.starlark.java.eval.Eval.execStatements(Eval.java:82)
	at net.starlark.java.eval.Eval.execFunctionBody(Eval.java:66)
	at net.starlark.java.eval.StarlarkFunction.fastcall(StarlarkFunction.java:173)
	at net.starlark.java.eval.Starlark.fastcall(Starlark.java:638)
	at net.starlark.java.eval.Starlark.execFileProgram(Starlark.java:928)
	at com.google.devtools.build.lib.packages.WorkspaceFactory.execute(WorkspaceFactory.java:157)
	at com.google.devtools.build.lib.skyframe.WorkspaceFileFunction.compute(WorkspaceFileFunction.java:375)
	at com.google.devtools.build.skyframe.AbstractParallelEvaluator$Evaluate.run(AbstractParallelEvaluator.java:571)
	at com.google.devtools.build.lib.concurrent.AbstractQueueVisitor$WrappedRunnable.run(AbstractQueueVisitor.java:382)
	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(Unknown Source)
	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(Unknown Source)
	at java.base/java.lang.Thread.run(Unknown Source)
    ```
