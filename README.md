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

For example, pushing the commit and tag for `v0.0.14` would be done like this:
```bash
git push --atomic origin master v0.0.14
```
