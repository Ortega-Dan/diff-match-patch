Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **Dart**.

Dart can either be run in the Dart VM, or it may be compiled to JavaScript.  Note that in the latter case, there's already a version of this library natively written in JavaScript.

### Hello World

Here's a minimal example of a diff in Dart:

```dart
import 'DiffMatchPatch.dart';

void main() {
  DiffMatchPatch dmp = new DiffMatchPatch();
  List<Diff> d = dmp.diff_main('Hello World.', 'Goodbye World.');
  // Result: [(-1, "Hell"), (1, "G"), (0, "o"), (1, "odbye"), (0, " World.")]
  dmp.diff_cleanupSemantic(d);
  // Result: [(-1, "Hello"), (1, "Goodbye"), (0, " World.")]
  print(d);
}
```

Go to the `dart` directory and save the above program as `hello.dart`.  Then execute `dart hello.dart`.

### Tests

Unit tests can be performed from the `dart/tests` directory by executing `dart DiffMatchPatchTest.dart`.  All tests should pass.

Speed test for diff can be performed from the `dart/tests` directory by executing `dart SpeedtestVM.dart`.

Alternatively, the speed test can be compiled to JavaScript.  Go to the `dart/tests` directory and execute `dart2js -O4 --out=Speedtest.dart.js Speedtest.dart`, then open `dart/tests/Speedtest.html` in a browser.