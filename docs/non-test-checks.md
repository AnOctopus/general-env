# Linting (pylint)
- Checks for code that is either directly an error, like using undefined variables, 
- Checks for code that is technically valid but indicates a likely bug, like unused arguments or failing to override abstract methods
- Checks for code that is unnecessary and makes the code harder to read/reason about, like wildcard imports or unused imports
- Modestly improves code correctness (fewer bugs) and readability of code (easier to understand/change)
# Typechecking (mypy)
- Checks that type annotations have been added to code and that code is consistent with them
- Reveals basic consistency errors
- Provides a maintained source of documentation about the shape/structure of data in the code
- Makes refactoring easier/safer (similar to how tests help refactoring)
# Code formatting (pycodestyle)
- Checks that code has a consistent formatting that adheres to a standard code style
- Reduces mental effort to read through code
- Low cost to have code satisfy this, with the use of formatting tools like Black
# Code coverage (pytest-cov and coverage)
- Checks how much of the code is executed by tests
- Improving code coverage reduces defects, and guides further test efforts towards places that aren't covered

# Ratcheting
- Ratcheting allows us to check existing codebases for how well they satisfy the above kinds of checks, and enforce gradual improvement, without forcing a bunch of work to make them completely pass up front
- I suspect that if I could spend one day heads down on implementing ratcheting, I could have it done with reasonable quality
