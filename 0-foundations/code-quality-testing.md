# Code Quality and Testing

## Concept Overview

* **Code Quality**: Refers to how well code adheres to standards, is readable, maintainable, and free of bugs.
* **Testing**: Verifying that code behaves as expected. Types include:

  * **Unit Testing**: Test individual functions or methods.
  * **Integration Testing**: Test interaction between components.
  * **End-to-End (E2E) Testing**: Simulate real user scenarios.
  * **Static Analysis**: Code is analyzed without executing it (e.g., linting).

## Real-World Use

* Teams enforce **code quality** using linters (ESLint, Flake8), formatters (Prettier, Black), and CI pipelines.
* **Unit tests** are written for business logic.
* **Integration tests** verify DB/service interaction.
* **E2E tests** ensure user flows work (e.g., using Cypress or Playwright).

## Common Pitfalls & Tips

* Writing tests **after development** often leads to poor coverage.
* Relying only on **E2E tests** makes the test suite fragile and slow.
* Good tests:

  * Are **isolated**, **deterministic**, and **fast**.
  * Follow **AAA (Arrange-Act-Assert)** structure.
  * Use **mocks/stubs** where needed.

## Interview Insights

* Questions to expect:

  * "What testing strategy does your team follow?"
  * "How do you ensure code is maintainable?"
  * "What tools do you use for testing?"
  * "How do you test edge cases and failures?"
* Emphasize:

  * Layered testing approach (unit → integration → E2E).
  * Code quality gates in CI (e.g., linting, test thresholds).
  * Refactoring code with high test coverage safely.

## Mini Scenario

> "You inherited a legacy module with no tests and are asked to refactor it. What do you do first?"
>
> 🔍 You should:
>
> * Write **characterization tests** to capture current behavior.
> * Gradually **refactor** with small commits.
> * Add **unit tests** around new/refactored logic.

## Hands-on Prompt

> * Write a simple function (e.g., `isPalindrome(str)`).
> * Add unit tests covering normal cases, edge cases, and invalid input.
> * Use a linter to ensure code style.
> * Refactor the function after tests pass to make it more readable.

## Further Reading

### Code Quality

* <a href="https://eslint.org/" target="_blank">ESLint (JavaScript Linting)</a>
* <a href="https://black.readthedocs.io/en/stable/" target="_blank">Black (Python Formatter)</a>
* <a href="https://deepsource.io/blog/static-analysis/" target="_blank">What is Static Analysis? – DeepSource Blog</a>

### Testing Frameworks & Best Practices

* <a href="https://jestjs.io/docs/getting-started" target="_blank">Jest (JavaScript Unit Testing)</a>
* <a href="https://docs.pytest.org/en/stable/" target="_blank">Pytest (Python Testing)</a>
* <a href="https://docs.cypress.io/" target="_blank">Cypress (End-to-End Testing)</a>
* <a href="https://playwright.dev/" target="_blank">Playwright (Modern E2E Testing)</a>
* <a href="https://martinfowler.com/articles/practical-test-pyramid.html" target="_blank">Martin Fowler – Test Pyramid</a>
