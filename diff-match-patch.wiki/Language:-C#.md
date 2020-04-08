Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **C#**.

C# can be executed either with Microsoft's Visual Studio, or with [Mono](http://www.mono-project.com/).  This documentation uses Mono.

### Hello World

Here's a minimal example of a diff in C#:

```c#
using DiffMatchPatch;
using System;
using System.Collections.Generic;

public class hello {
  public static void Main(string[] args) {
    diff_match_patch dmp = new diff_match_patch();
    List<Diff> diff = dmp.diff_main("Hello World.", "Goodbye World.");
    // Result: [(-1, "Hell"), (1, "G"), (0, "o"), (1, "odbye"), (0, " World.")]
    dmp.diff_cleanupSemantic(diff);
    // Result: [(-1, "Hello"), (1, "Goodbye"), (0, " World.")]
    for (int i = 0; i < diff.Count; i++) {
      Console.WriteLine(diff[i]);
    }
  }
}
```

Go to the `csharp` directory and save the above program as `hello.cs`.  Then execute two commands:
```
mcs hello.cs DiffMatchPatch.cs
mono hello.exe
```

### Tests

Unit tests can be performed from the `csharp/tests` directory by executing two commands:
```
mcs DiffMatchPatchTest.cs ../DiffMatchPatch.cs
mono DiffMatchPatchTest.exe
```
All tests should pass.

Speed test for diff can be performed from the `csharp/tests` directory by two commands:
```
mcs Speedtest.cs ../DiffMatchPatch.cs
mono Speedtest.exe
```