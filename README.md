# ML/I macroprocessor implementation for TOPS-10

## More about ML/I and macroprocessors
- http://www.ml1.org.uk/index.html
- https://en.wikipedia.org/wiki/ML/I
- https://en.wikipedia.org/wiki/General-purpose_macro_processor

## More about TOPS-10 and historical simulation
- https://en.wikipedia.org/wiki/TOPS-10
- https://en.wikipedia.org/wiki/SIMH

## To see it in action
- You must have a working TOPS-10 host with MACRO-10 and LINK-10 support.
- You must have a means to move text files into a TOPS-10 (Kermit).
- Copy all files into a build directory.
- Issue command "DO CLEAN" then "DO BUILD"
- ML/I executable is MLI.exe.
- Issue command "DO TEST"

## Status of this implementation
- This implementation passes all LOWL and ML/I test suites.
- This implementation has no command scanner.
- Lots of cleanup needed in code, cross-references, and build support.

## Comments welcome to Calvin Miracle, cbmira01@gmail.com
