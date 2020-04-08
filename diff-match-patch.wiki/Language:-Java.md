Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **Java**.

Before starting, go to the `java` directory, and create an empty sub-directory called `classes`.

### Hello World

Here's a minimal example of a diff in Java:

```java
import java.util.LinkedList;
import name.fraser.neil.plaintext.diff_match_patch;

public class hello {
  public static void main(String args[]) {
    diff_match_patch dmp = new diff_match_patch();
    LinkedList<diff_match_patch.Diff> diff = dmp.diff_main("Hello World.", "Goodbye World.");
    // Result: [(-1, "Hell"), (1, "G"), (0, "o"), (1, "odbye"), (0, " World.")]
    dmp.diff_cleanupSemantic(diff);
    // Result: [(-1, "Hello"), (1, "Goodbye"), (0, " World.")]
    System.out.println(diff);
  }
}
```

Go to the `java/src` directory and save the above program as `hello.java`.  Then go to the `java` directory and execute these two commands:
```
javac -d classes src/name/fraser/neil/plaintext/diff_match_patch.java src/hello.java
java -classpath classes hello
```

### Tests

Unit tests can be performed from the `java` directory by executing two commands:
```
javac -d classes src/name/fraser/neil/plaintext/diff_match_patch.java tests/name/fraser/neil/plaintext/diff_match_patch_test.java
java -classpath classes name/fraser/neil/plaintext/diff_match_patch_test
```
All tests should pass.

Speed test for diff can be performed from the `java` directory by executing two commands:
```
javac -d classes src/name/fraser/neil/plaintext/diff_match_patch.java tests/name/fraser/neil/plaintext/Speedtest.java
java -classpath classes name/fraser/neil/plaintext/Speedtest
```