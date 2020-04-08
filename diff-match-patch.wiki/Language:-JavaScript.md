Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **JavaScript**.

`javascript/diff_match_patch_uncompressed.js` is the human-readable version.  This should be used by developers and Node.js.

`javascript/diff_match_patch.js` has been compressed using [Google's Closure Compiler](https://closure-compiler.appspot.com/home) on 'simple' mode.  This reduces the size to 25% of the uncompressed version.

The JavaScript version has no dependencies.  It works in Netscape 4, Internet Explorer 5.5, and all browsers released since the year 2000 (the limiting factor is the use of the `encodeURI` function).

### Hello World

Here's a minimal example of a diff in JavaScript:

```html
<html>
  <body>
    <script src="diff_match_patch.js"></script>
    <script>
      var dmp = new diff_match_patch();
      var diff = dmp.diff_main('Hello World.', 'Goodbye World.');
      // Result: [(-1, "Hell"), (1, "G"), (0, "o"), (1, "odbye"), (0, " World.")]
      dmp.diff_cleanupSemantic(diff);
      // Result: [(-1, "Hello"), (1, "Goodbye"), (0, " World.")]
      alert(diff);
    </script>
  </body>
</html>
```

Save the above as an HTML file in the `javascript` directory, then open the file in any web browser.

### Tests

Unit tests can be performed by pointing a web browser at `javascript/tests/diff_match_patch_test.html`.  Over a hundred tests should run, with zero failures.

Speed test for diff can be performed by pointing a web browser at `javascript/tests/speedtest.html` and pressing "Compute Diff".