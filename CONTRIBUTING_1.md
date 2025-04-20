<h1 align="center" style="border-bottom: none;">Contributing to our Proof of SQL Repository</h1>
<p align="center">
  <a href="https://www.conventionalcommits.org/en/v1.0.0/">
    <img alt="semantic-release: conventional-commits" src="https://img.shields.io/badge/semantic--release-conventional--commits-blueviolet">
  </a>
</p>

The following guideline is heavily based on the [Angular Project Guideline](https://github.com/angular/angular/blob/main/CONTRIBUTING.md). As a contributor, here are the rules we would like you to follow:

 - [Notice](#notice)
 - [Submission Guidelines](#submit)
   - [Submitting a Pull Request (PR)](#submit-pr)
   - [Addressing review feedback](#address-review)
   - [Updating the commit message](#updating-commit-message)
   - [After your pull request is merged](#after-pr-merged)
 - [Coding Rules](#rules)
 - [Commit Message Guidelines](#commit-guidelines)
   - [Commit Message Format](#commit)
   - [Revert Commits](#revert)
   - [Commit Examples](#commit-examples)
   - [Automatic Semantic Release](#semantic-release)

## <a name="notice"></a> Notice

When you contribute code, you affirm that the contribution is your original work and that you license the work to the project under the project's open source license. Whether or not you state this explicitly, by submitting any copyrighted material via pull request, email, or other means you agree to license the material under the project's open source license and warrant that you have the legal authority to do so.


## <a name="submit"></a> Submission Guidelines

The general flow you can follow when implementing a new feature/bugfix/docs/test is:

1. Create a GitHub issue to keep track of the task you are implementing.
 
    The most relevant fields in the issue are: `assignees`, `projects`, `milestone`, `development`, and `description`. Those fields are not mandatory, but they may help in the future to easily fetch information related to a specific feature, such as the time it took from implementation until completeness, and which PRs are associated with which feature (many PRs can be related to a single feature/issue).

2. From the created issue panel, use the `main` branch to generate a new branch that will be tied with the issue. In this case, when a Pull Request tied with the branch is merged, the issue will be automatically closed.

3. Whenever you are done implementing the modifications in your branch, make a Pull Request to merge your changes into the main branch. Try to always assign someone to review your Pull Request. Since we are using an automatic release process to version our code, you should follow a strict pattern in your commit messages (below for more descriptions). It is advised that you name your Pull Request according to our semantic release rules, given that the commit message is automatically the same as the Pull Request title. For instance, name the PR as "feat: add hadamard product" and do not name the PR as "Adding hadamard product". Always test your code locally before any pull request is submitted.

4. In the case of many commit messages to your branch, force the Pull Request to merge as a squashed merge.

5. After the merge is done, delete your branch from the repository and check that related issues were indeed closed.

### <a name="submit-pr"></a> Submitting a Pull Request (PR)

Before you submit your Pull Request (PR) consider the following guidelines:

1. Make your changes in a new git branch:

    In case you haven't generated a new branch yet, use the following command to create a new branch from the main:

    ```bash
    git checkout -b my-feature-branch main
    ```
    
    Otherwise, only checkout your branch:

    ```bash
    git checkout my-feature-branch
    ```

2. Create your patch, **including appropriate test cases**.

3. Follow our [Coding Rules](#rules).

4. <a name="test-suite"></a>Run the entire test suite to ensure tests are passing.

5. <a name="code-quality-checks"></a>When applicable, run the code quality checks locally so that the code is not only correct but also clean.

6. Commit your changes using a descriptive commit message that follows our [commit message conventions](#commit). Adherence to these conventions is necessary because release notes are automatically generated from these messages.

    ```bash
    git add <modified files>
    git commit
    ```

    Note: Only add relevant files. Avoid adding binary files, as they frequently waste storage resources. Consider adding only text files (.rs, .cc, .json, .toml, etc). Files that should NOT be committed should instead be added
    to `.gitignore`.

7.  Push your branch to GitHub:

    ```bash
    git push origin my-feature-branch
    ```

8.  In GitHub, send a pull request to `sxt-proof-of-sql:main`.

    Our proof of SQL repository triggers automatically a workflow to test the code whenever a Pull Request is submitted or a commit is pushed to an existing PR. Before closing the PR, always verify that those tests are indeed passing.

    NOTE: <a name="ci-review-note"></a>**We will not review a PR if CI (except for `Check Approver` since this requires a review) doesn't pass. We are happy to help you if you can't figure out how to get the CI to pass but it is your responsibility to make sure they pass.**

    Also, to ease this process of using git, you can try to use [vscode](https://code.visualstudio.com/). Vscode has some nice extensions to manage your git workflow.

### <a name="address-review"></a> Addressing review feedback

If we ask for changes via code reviews then:

1. Make the required updates to the code.

2. [Re-run the entire test suite](#test-suite) to ensure tests are still passing.

3. [Re-run the code quality checks](#code-quality-checks) to ensure that the code is still clean.

4. Create a fixup commit and push to your GitHub repository (this will update your Pull Request):

    ```shell
    # Create a fixup commit to fix up the last commit on the branch:
    git commit --all --fixup HEAD
    git push
    ```

    or

    ```shell
    # Create a fixup commit to fix up commit with SHA <COMMIT_SHA>:
    git commit --fixup <SHA>
    ```

    For more info on working with fixup commits see [here](https://github.com/angular/angular/blob/main/docs/FIXUP_COMMITS.md).

5. In order to ensure that we do not pollute the main branch with poorly written commit messages, before the PR can be merged, we require that the commits in your branch be clean. In particular, this means that you should rebase instead of merge in order to catch up to main. Additionally, any commits of the variety `address review comments` should be turned into a fixup commit instead.

### <a name="updating-commit-message"></a> Updating the commit message

A reviewer might often suggest changes to a commit message (for example, to add more context for a change or adhere to our [commit message guidelines](#commit)).
In order to update the commit message of the last commit on your branch:

1. Check out your branch:

    ```shell
    git checkout my-fix-branch
    ```

2. Amend the last commit and modify the commit message:

    ```shell
    git commit --amend
    ```

3. Push to your GitHub repository:

    ```shell
    git push --force-with-lease
    ```

NOTE: If you need to update the commit message of an earlier commit, you can use `git rebase` in interactive mode. See the [git docs](https://git-scm.com/docs/git-rebase#_interactive_mode) for more details.

### <a name="after-pr-merged"></a> After your pull request is merged

After your pull request is merged, you can safely delete your branch and pull the changes from the main (upstream) repository:

* Delete the remote branch on GitHub either through the GitHub web UI or your local shell as follows:

    ```shell
    git push origin --delete my-fix-branch
    ```

* Check out the main branch:

    ```shell
    git checkout main -f
    ```

* Delete the local branch:

    ```shell
    git branch -D my-fix-branch
    ```

* Update your local `main` with the latest upstream version:

    ```shell
    git pull --ff upstream main
    ```

## <a name="rules"></a> Coding Rules
To ensure consistency throughout the source code, keep these rules in mind as you are working:

* All features or bug fixes **must be tested** by one or more specs (unit-tests). 
* All public API methods **must be documented**.

## <a name="commit-guidelines"></a> Commit Message Guidelines

### <a name="semantic-version"></a> Semantic Versioning

To version our code, we follow an **automatic semantic versioning** given by the [Semantic Versioning](https://semver.org/) scheme, which establishes that the version is given by **"MAJOR.MINOR.PATCH"** number, which is updated as:

1. Increase the **MAJOR** version when you make incompatible API changes.
2. Increase the **MINOR** version when you add functionality in a backwards compatible manner.
3. Increase the **PATCH** version when you make backwards compatible bug fixes.

For instance: "1.1.3" is a program that is in the first major and minor version and the third patch version. When an incompatible change is done to the public API, then this version is updated to "2.0.0". If a backward compatible feature is added later, the version is updated to "2.1.0".

### <a name="commit"></a> Commit Message Format

We follow a strict commit message format inspired by [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).. This improves readability, automates semantic versioning, and keeps history clean.

#### **Commit format:**

```
<type>[!]: <short summary>
<BLANK LINE>
<optional body>
<BLANK LINE>
<optional footer>
```

#### **Header (Required)**
- `<type>`: Commit type (see list below).
- Add `!` after `<type>` for **a breaking changes**
- `<summary>`: Short description:
    - Present tense (e.g., "add", not "added")
    - Less than 80 characters
    - No capitalization or period

**Commit Types**

Each commit must use one of the following types:

| Type        | Description                                                                 | SemVer Impact |
|-------------|-----------------------------------------------------------------------------|----------------|
| `feat`      | Introduces a new feature                                                    | MINOR          |
| `feat!`     | New feature with breaking changes                                           | MAJOR          |
| `fix`       | Patches a bug                                                               | PATCH          |
| `fix!`      | Bug fix with breaking changes                                               | MAJOR          |
| `perf`      | Improves performance without behavior change                                | PATCH          |
| `perf!`     | Performance improvement with breaking changes                               | MAJOR          |
| `refactor`  | Code change that doesn't fix bugs or add features                           | PATCH          |
| `refactor!` | Refactoring with breaking changes                                           | MAJOR          |
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

#### **Body (Optional)**
- Use present tense: “fix” not “fixed”
- Explain the reason for the change and context
- Compare previous vs. new behavior if helpful

#### **Footer (Optional)**
Use for:
- Breaking changes or deprecations:
    ```
    BREAKING CHANGE: changed response format in /v1/login
    ```

- Issue references:
    ```
    Closes #123
    ```

### <a name="revert"></a>Revert commits

If the commit reverts a previous commit, it should begin with `revert:`
- Header:
    ```
    revert: <original commit header>
    ```
- The content of the commit message body should contain:
    - information about the SHA of the commit being reverted
    - a clear description of the reason for reverting the commit message.

    ```
    This reverts commit <SHA>.
    Reason: <why it was reverted>
    ```

## <a name="commit-examples"></a>Commit Examples

Commit message with ! to draw attention to breaking change

```
feat!: send an email to the customer when a product is shipped
```

Commit message with both ! and BREAKING CHANGE footer

```
chore!: drop support for Node 6

BREAKING CHANGE: use JavaScript features not available in Node 6.
```

Commit message with description and breaking change in the footer

```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

Commit message with no body

```
docs: correct spelling of CHANGELOG
```

Commit message for a fix using an (optional) issue number.

```
fix: minor typos in code

see the issue for details on the typos fixed

fixes issue #12
```

## <a name="semantic-release"></a>Automatic Semantic - Release Process

We are using a node semantic-release tool to automatically trigger our release process. As shown below, this tool inspects the commitment message to decide if the release should be triggered and which type of release should be triggered:

| Type     | Message                                                                                                                                                                                       | Release Type                                                                                                  |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| ci       | ci:                                                                                                                                                                                           | No Release                                                                                                    |
| docs     | docs:                                                                                                                                                                                         | No Release                                                                                                    |
| refactor | refactor:                                                                                                                                                                                     | No Release                                                                                                    |
| test     | test: add new unit tests to gpu commitment module                                                                                                                                             | No Release                                                                                                    |
| build    | build:                                                                                                                                                                                        | Fix Release (Patch)                                                                                                    |
| perf      | perf: speedup gpu commitment by 3x                                                                                                                                    | Fix Release (Patch)                                                                                           |
| fix      | fix: stop graphite breaking when too much pressure applied                                                                                                                                    | Fix Release (Patch)                                                                                           |
| feat     | feat: graphiteWidth' option                                                                                                                                                                   | Feature Release (Minor)                                                                                       |
| feat     | feat: add graphiteWidth option<br><br><body> The default graphite width of 10mm is always used for performance reasons.<br><br>BREAKING CHANGE: The graphiteWidth option has been added. | Breaking Release (Major)<br><br>(Note that the BREAKING CHANGE:<br>token must be in the footer of the commit) |
| perf     | perf: remove graphiteWidth option<br><br><body> The default graphite width of 10mm is always used for performance reasons.<br><br>BREAKING CHANGE: The graphiteWidth option has been removed. | Breaking Release (Major)<br><br>(Note that the BREAKING CHANGE:<br>token must be in the footer of the commit) |

Check the [Semantic-Release](https://github.com/semantic-release/semantic-release) link for more info. Ps: to update the above rules, check the [package.json](package.json) file, in the `release -> plugins -> @semantic-release/commit-analyzer -> releaseRules` section.
