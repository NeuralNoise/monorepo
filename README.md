# monorepo

I had to rebuild my dev environment from scratch while my computer is out for
repairs. So I thought... why not try submodules and some top-level tooling.

So far, not so bad.

## Requirements

* docker (I've only run this against the docker for mac beta)
* git
* probably other things I forgot I have installed

## Install

Run `docker ps` to make sure all your other containers are stopped.

```
git clone --recursive git@github.com:theonion/monorepo.git
cd monorepo
scripts/run onion init
```

## scripts

```
git submodule foreach SHELL_COMMAND

Do anything in every submodule

git submodule foreach ls
git submodule foreach git status
git submodule foreach rm -rf ./ # NO!, but you could
```

```
scripts/run PROJECT SCRIPT [args]

You can run any script in a sub-project's `scripts/` directory:

scripts/run onion serve
scripts/run onion link --python django-bulbs
```

```
scripts/dc PROJECT [args]

An alias for docker-compose that runs in the context of a sub-project's docker-compose.yml.

scripts/dc onion ps
scripts/dc onion kill
```

```
scripts/git PROJECT [args]

An alias to run git commands in a sub-repository.

This script is annoying, you lose git completion.
But it's handy in a pinch to see what's up in your sub repo without cd'ing into it.

scripts/git onion status
scripts/git onion add -u
scripts/git onion commit -m "Commit message."
scripts/git onion push
```

```
scripts/status

Print out git status for all sub repos.
Tells you what branch the repo is on, and what changes are present/need to be comitted.
```

```
scripts/update-modules

Big dangerous script. Be careful.

Runs through all sub-projects, checks out master and does a git pull.
```
