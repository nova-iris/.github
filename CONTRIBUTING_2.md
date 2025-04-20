<h1 align="center" style="border-bottom: none;">Contributing to our Repository</h1>
<p align="center">
  <a href="https://www.conventionalcommits.org/en/v1.0.0/">
    <img alt="semantic-release: conventional-commits" src="https://img.shields.io/badge/semantic--release-conventional--commits-blueviolet">
  </a>
</p>

This guideline is inspired by the [Angular Project Guideline](https://github.com/angular/angular/blob/main/CONTRIBUTING.md). We welcome contributions and appreciate your efforts to improve the project. Please follow the guidelines below to ensure a smooth contribution process.

## Table of Contents
- [Notice](#notice)
- [Submission Guidelines](#submission-guidelines)
  - [Submitting a Pull Request (PR)](#submitting-a-pull-request-pr)
  - [Addressing Review Feedback](#addressing-review-feedback)
  - [Updating Commit Messages](#updating-commit-messages)
  - [After Your Pull Request is Merged](#after-your-pull-request-is-merged)
- [Coding Rules](#coding-rules)
- [Commit Message Guidelines](#commit-message-guidelines)
  - [Semantic Versioning](#semantic-versioning)
  - [Commit Message Format](#commit-message-format)
  - [Revert Commits](#revert-commits)
  - [Commit Examples](#commit-examples)
- [Automatic Semantic Release](#automatic-semantic-release)

---

## Notice

When contributing to this repository, you affirm that the contribution is your original work and that you license it under the project's open-source license. Contributions made to this repository must adhere to the guidelines outlined below.

---

## Submission Guidelines

### General Workflow

1. **Create an Issue**:
   - Open a GitHub issue to track the task you are implementing.
   - Fill in relevant fields: `assignees`, `projects`, `milestone`, `description`, etc. (optional but helpful).

2. **Create a Branch**:
   - Base your branch on the `main` branch and tie it to the issue.
   - Example branch name: `feature/#123-add-authentication`.

3. **Develop and Test**:
   - Implement the feature, bugfix, or documentation.
   - Include appropriate test cases and follow the [Coding Rules](#coding-rules).

4. **Submit a Pull Request (PR)**:
   - Make a PR to merge your changes into the `main` branch.
   - Assign reviewers to your PR and ensure it passes CI checks.

5. **Merge and Cleanup**:
   - After your PR is merged, delete your branch and verify the related issue is closed.

### Submitting a Pull Request (PR)

Before submitting a PR:

1. **Create a Branch**:
   ```bash
   git checkout -b my-feature-branch main
   ```

2. **Add Changes**:
   - Include appropriate test cases.
   - Follow coding rules and style guidelines.

3. **Run Tests**:
   - Ensure all tests pass and run quality checks locally.

4. **Commit Your Changes**:
   - Use descriptive commit messages following [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

5. **Push and Open a PR**:
   ```bash
   git push origin my-feature-branch
   ```
   - Open a PR to `main` and ensure CI checks pass before requesting a review.

---

### Addressing Review Feedback

If requested changes are needed during the review process:

1. Update your code.
2. Re-run tests and quality checks.
3. Add a fixup commit for minor changes:
   ```bash
   git commit --fixup <SHA>
   ```
4. Ensure commits are clean before merging:
   ```bash
   git rebase -i --autosquash main
   ```

---

### Updating Commit Messages

To update a commit message:

1. Amend the last commit:
   ```bash
   git commit --amend
   git push --force-with-lease
   ```

2. For earlier commits, use interactive rebase:
   ```bash
   git rebase -i HEAD~n
   ```

---

### After Your Pull Request is Merged

1. Delete the remote branch:
   ```bash
   git push origin --delete my-fix-branch
   ```

2. Update your local `main` branch:
   ```bash
   git checkout main
   git pull --ff upstream main
   ```

---

## Coding Rules

To ensure consistency across the project:

1. **Testing**:
   - All features and bug fixes must include test cases.
2. **Documentation**:
   - Document all public API methods and major changes.
3. **Code Style**:
   - Use the project's preferred linting and formatting tools (e.g., Prettier, ESLint).

---

## Commit Message Guidelines
### Semantic Versioning
To version the code, the repository follows [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) using the scheme MAJOR.MINOR.PATCH:

1. MAJOR: Incremented for incompatible API changes.
2. MINOR: Incremented for backwards-compatible new features.
3. PATCH: Incremented for backwards-compatible bug fixes.

For instance, version 1.1.3 indicates the first major version, first minor version, and the third patch version. When incompatible changes are introduced, the version increments to the next major version.

### Commit Message Format

```
<type>[!]: <short summary>
<BLANK LINE>
<optional body>
<BLANK LINE>
<optional footer>
```

#### Header
- `<type>`: Commit type (e.g., `feat`, `fix`, `docs`).
- `!`: Add `!` for breaking changes.
- `<summary>`: Short description (max 80 characters).

#### Commit Types
| Type        | Description                                                                 | SemVer Impact |
|-------------|-----------------------------------------------------------------------------|----------------|
| `feat`      | Introduces a new feature                                                    | MINOR          |
| `fix`       | Patches a bug                                                               | PATCH          |
| `perf`      | Improves performance without behavior change                                | PATCH          |
| `refactor`  | Code change that doesn't fix bugs or add features                           | PATCH          |
| `test`      | Adds or updates tests                                                       | None           |
| `bench`     | Adds or updates benchmarks                                                  | None           |
| `build`     | Changes to build system or dependencies                                     | PATCH          |
| `ci`        | CI configuration or scripts                                                 | None           |
| `docs`      | Documentation changes only                                                  | PATCH          |
| `style`     | Code formatting, whitespace, etc. (no logic change)                         | None           |
| `chore`     | Routine tasks like dependency updates, cleanup                              | None           |


**Tips**
- Keep commits focused — don’t mix unrelated changes.
- If adding a feature and related tests, use separate commits:
    ```
    feat: add user registration endpoint
    test: add tests for registration flow
    ```
    
#### Body (Optional)
- Use present tense: “fix” not “fixed”
- Explain the reason for the change and context
- Compare previous vs. new behavior if helpful

#### Footer (Optional)
- Breaking changes:
   ```
   BREAKING CHANGE: changed response format in /v1/login
   ```
- Issue references:
   ```
   Closes #123
   ```

---

### Revert Commits

To revert a commit:
```
revert: <original commit header>

This reverts commit <SHA>.
Reason: <why it was reverted>.
```

---

### Commit Examples

- Feature with breaking changes:
  ```
  feat!: add support for new API endpoint

  BREAKING CHANGE: Updated API version to v2.
  ```

- Bug fix:
  ```
  fix: resolve null reference in user service
  ```

- Documentation update:
  ```
  docs: update contributing file with branch naming conventions
  ```

---

## Automatic Semantic Release

We use [Semantic Release](https://github.com/semantic-release/semantic-release) to automate versioning and changelog generation based on commit messages. Ensure your commit messages follow the [Commit Message Guidelines](#commit-message-guidelines).

---

Let me know if you need further assistance refining this document!