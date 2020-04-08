Each language port of Diff Match Patch uses the [same API](API).  These are the language-specific notes regarding **Objective-C**.

Open the `objectivec/DiffMatchPatch.xcodeproj` file using Xcode (version 9.2 is known to work).

### Tests

Unit tests can be performed by choosing "DiffMatchPatchTest" from the list of schemes.  Click on the diamond-shaped test navigator icon.  Right-click on "DiffMatchPatchTest" in the navigator and choose "Run".  Over twenty test groups should run, with zero failures.

Speed test for diff can be performed by choosing "speedtest" from the list of schemes.  Click the "Run" button.