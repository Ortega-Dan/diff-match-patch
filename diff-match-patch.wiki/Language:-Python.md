Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **Python**.

Python comes in two incompatible flavours; Python 2 and Python 3.  Choose the version that's compatible with your interpreter.  Python 2 is somewhat faster than Python 3.  Type `python --version` to find out which version your system has installed.

### Hello World

Here's a minimal example of a diff in Python:

```python
import diff_match_patch as dmp_module

dmp = dmp_module.diff_match_patch()
diff = dmp.diff_main("Hello World.", "Goodbye World.")
# Result: [(-1, "Hell"), (1, "G"), (0, "o"), (1, "odbye"), (0, " World.")]
dmp.diff_cleanupSemantic(diff)
# Result: [(-1, "Hello"), (1, "Goodbye"), (0, " World.")]
print(diff)
```

Go to the `python2` or `python3` directory and save the above program as `hello.py`.  Then execute `python hello.py`.

### Tests

Unit tests can be performed from the `python/tests` directory by executing `python diff_match_patch_test.py`.  Over twenty test groups should run, with zero failures.

Speed test for diff can be performed from the `python/tests` directory by executing `python speedtest.py`.  It takes about 20 seconds.