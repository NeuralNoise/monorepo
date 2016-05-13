# monorepo

I had to rebuild my dev environment from scratch while my computer is out for
repairs. So I thought... why not try submodules and some top-level tooling.

So far, not so bad.

```
git clone --recursive git@github.com:theonion/monorepo.git
scripts/run onion init
```

You can run any script in a project's `scripts/` directory.

```
scripts/run PROJECT SCRIPT [args]
scripts/run onion serve
scripts/run onion link --python django-bulbs
```
