Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **Lua**.

A critical note with Lua is that (unlike most other languages) it does not have any awareness of Unicode.  Thus:

```string.len("中国") → 6```

Strings in Lua are treated as a series of bytes, not a series of characters.  This means that the functions in Diff Match Patch may return unexpected and non-printable results as it splits characters at the byte level.

A side effect of the lack of Unicode support is that the line-mode speedup in diff is not available.

### Hello World

Here's a minimal example of a diff in Lua:

```lua
local dmp = require 'diff_match_patch'

diff = dmp.diff_main('Hello World.', 'Goodbye World.')
-- Result: [(-1, "Hell"), (1, "G"), (0, "o"), (1, "odbye"), (0, " World.")]
dmp.diff_cleanupSemantic(diff)
-- Result: [(-1, "Hello"), (1, "Goodbye"), (0, " World.")]
for i,tuple in ipairs(diff) do
  print('(' .. tuple[1] .. ', ' .. tuple[2] .. ')')
end
```

Go to the `lua` directory and save the above program as `hello.lua`.  Then execute `lua hello.lua`.

### Tests

Unit tests can be performed from the `lua/tests` directory by executing `lua diff_match_patch_test.lua`.  Over twenty test groups should run, with zero failures.

Speed test for diff can be performed from the `lua/tests` directory by executing `lua speedtest.lua`.  It takes about 15 seconds.