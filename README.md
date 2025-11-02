# bitbully-databases
Opening Databases for the Board Game Connect-4.


# Development (Debian-based Systems)

## Install & Activate virtualenv

```bash
python3 -m venv venv
source venv/bin/activate
```

## Install Dependencies

```bash
pip install -e .[dev,ci]
```

```bash
pre-commit install
```

You can run pre-commit before a commit with:

```bash
pre-commit run
```

## Commitizen

### Bump Version

```bash
cz bump --dry-run # first perform a dry run
cz bump
git push origin tag x.x.x
```

### Push commit and tag atomically

```bash
git push --atomic origin master v0.0.14
```

### Commit types

| Commit Type | Title                    | Description                                                                                                 | Emoji |
|-------------|--------------------------|-------------------------------------------------------------------------------------------------------------|:-----:|
| `feat`      | Features                 | A new feature                                                                                               |   ✨   |
| `fix`       | Bug Fixes                | A bug Fix                                                                                                   |  🐛   |
| `docs`      | Documentation            | Documentation only changes                                                                                  |  📚   |
| `style`     | Styles                   | Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)      |  💎   |
| `refactor`  | Code Refactoring         | A code change that neither fixes a bug nor adds a feature                                                   |  📦   |
| `perf`      | Performance Improvements | A code change that improves performance                                                                     |  🚀   |
| `test`      | Tests                    | Adding missing tests or correcting existing tests                                                           |  🚨   |
| `build`     | Builds                   | Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)         |  🛠   |
| `ci`        | Continuous Integrations  | Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs) |  ⚙️   |
| `chore`     | Chores                   | Other changes that don't modify src or test files                                                           |  ♻️   |
| `revert`    | Reverts                  | Reverts a previous commit                                                                                   |  🗑   |
