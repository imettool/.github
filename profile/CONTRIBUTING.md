# Contributing to IMET

Thank you for considering contributing to IMET! We appreciate your interest in making this project better and welcome your contributions. 
The following rules and guidelines apply to all the repositories.

## How to Contribute

To contribute to the project, follow these steps:

1. **Fork the repository**: Fork the repository to your own account. This will create a copy of the project under your account.

2. **Clone the repository**: Clone the forked repository to your local machine using `git clone`. This allows you to work on the project locally.

3. **Create a branch**: Before making any changes, create a new branch in the repository. The branch name should be descriptive and reflect the changes you plan to make.

4. **Make changes**: Make your desired changes and improvements to the project. Please ensure that your changes adhere to the coding guidelines and best practices of the project.

5. **Test your changes**: Test your changes thoroughly to ensure they work as intended and do not introduce any new issues.

6. **Commit your changes**: Once you are satisfied with your changes, commit them with clear and concise commit messages that explain the purpose of the changes.

7. **Pull Request**: Push your changes to your forked repository and create a Pull Request (PR) to the `main` branch of the original repository. Provide a detailed description of the changes you made, the problem you solved, and any other relevant information.

8. **Code Review**: The project maintainers will review your Pull Request. Be prepared to make changes or address any feedback you receive during the review process.

9. **Merge**: Once your Pull Request has been approved and any necessary changes have been made, it will be merged into the main project. Congratulations on your successful contribution!

## Code Style and Guidelines

### Coding standards and conventions

IMET is built on top of [Laravel](https://laravel.com) and we expect contributions to follow, as closely as possible, the conventions and best practices commonly shared in the Laravel community.

- **Follow the Laravel way**: prefer framework-native solutions (Eloquent, Form Requests, Resources, Policies, Jobs, Events, Service Container, etc.) over custom abstractions. If Laravel provides a built-in tool for the job, use it.
- **PSR compliance**: code must adhere to [PSR-1](https://www.php-fig.org/psr/psr-1/), [PSR-4](https://www.php-fig.org/psr/psr-4/) and [PSR-12](https://www.php-fig.org/psr/psr-12/).
- **Naming conventions**: follow the conventions described in the [Laravel documentation](https://laravel.com/docs) and popularized resources such as [Laravel Best Practices](https://github.com/alexeymezenin/laravel-best-practices) — singular `Eloquent` model names, plural table names, camelCase methods, snake_case database columns, etc.
- **Strict typing**: declare `declare(strict_types=1);` at the top of every PHP file and type-hint arguments, return types and properties whenever possible.
- **Small, focused classes and methods**: respect the *Single Responsibility Principle*. Prefer Form Requests for validation, Action/Service classes for business logic and keep controllers thin.
- **Avoid premature abstractions**: write the simplest code that solves the problem at hand. Refactor only when a real need emerges.
- **Localization**: never hard-code user-facing strings; use the translation helpers (`__()`, `trans()`) and add the corresponding keys to the language files.
- **Frontend code**: Vue 3 components must follow the [Vue.js Style Guide](https://vuejs.org/style-guide/) (Composition API, `<script setup>`, PascalCase component names). Tailwind classes should be kept readable and grouped logically.

Code formatting is automated via [Laravel Pint](https://laravel.com/docs/pint). Before opening a PR, run:

```bash
composer pint
```

### Code quality and testing

We rely on a small set of tools to keep the codebase healthy. All of them must pass before a Pull Request can be merged.

- **[Pest](https://pestphp.com)** — the test framework used across all IMET repositories. Every new feature or bug fix should ship with tests:
    - Use **Feature tests** to cover HTTP endpoints, commands and integration points.
    - Use **Unit tests** for pure logic that does not require the framework.
    - Favor expressive, readable expectations (`expect(...)`) and Pest's higher-order syntax.
    - Use factories and the `RefreshDatabase` trait to keep tests isolated and reproducible.

  ```bash
  composer test
  ```

- **[PHPStan](https://phpstan.org)** (via [Larastan](https://github.com/larastan/larastan)) — static analysis. Contributions must not introduce new errors at the project's configured level.

  ```bash
  composer phpstan
  ```

- **[Rector](https://getrector.com)** — automated refactoring and upgrade rules. Run it to catch deprecations and apply safe modernizations:

  ```bash
  composer rector
  ```

- **[Pint](https://laravel.com/docs/pint)** — opinionated PHP code style fixer (Laravel preset).

  ```bash
  composer pint
  ```

> [!TIP]
> Before pushing your changes, run the full quality suite locally — `pint`, `rector`, `phpstan` and `pest` — to mirror what CI will execute on your Pull Request.

When fixing a bug, please add a regression test that fails without your fix and passes with it. When adding a feature, the related tests should describe the expected behavior clearly enough to serve as living documentation.
