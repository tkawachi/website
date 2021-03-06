Running commands
================

sbt interprets each command line argument provided to it as a command
together with the command's arguments. Therefore, to run a command that
takes arguments in batch mode, quote the command and its arguments. For
example,

``` {.sourceCode .console}
$ sbt 'project X' clean '~ compile'
```

Multiple commands can be scheduled at once by prefixing each command
with a semicolon. This is useful for specifying multiple commands where
a single command string is accepted. For example, the syntax for
triggered execution is \~ \<command\>. To have more than one command run
for each triggering, use semicolons. For example, the following runs
clean and then compile each time a source file changes:

``` {.sourceCode .console}
> ~ ;clean;compile
```

The \< command reads commands from the files provided to it as
arguments. Run help \< at the sbt prompt for details.

The alias command defines, removes, and displays aliases for commands.
Run help alias at the sbt prompt for details.

Example usage:

``` {.sourceCode .console}
> alias a=about
> alias
    a = about    
> a
[info] This is sbt ...
> alias a=
> alias
> a
[error] Not a valid command: a ...
```

The eval command compiles and runs the Scala expression passed to it as
an argument. The result is printed along with its type. For example,

``` {.sourceCode .console}
> eval 2+2
4: Int
```

Variables defined by an eval are not visible to subsequent evals,
although changes to system properties persist and affect the JVM that is
running sbt. Use the Scala REPL (console and related commands) for full
support for evaluating Scala code interactively.
