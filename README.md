knowtifier
==========

Heroku robot to check for releases or new rOpenSci packages.

## what it does

* get list of ropensci packages from <https://github.com/ropensci/roregistry>
* check if any new packages, or new versions, for each package:
    * if a new package, or a new release send email/tweet
    * if nothing new, skip

## Install

```
git clone git@github.com:ropenscilabs/knowtifier.git
cd knowtifier
```

## Setup

Create the app (use a different name, of course)

```
heroku apps:create ropensci-knowtifier
```

Push your app to Heroku

```
git push heroku master
```

Add the scheduler to your heroku app

```
heroku addons:create scheduler:standard
heroku addons:open scheduler
```

Add the task ```rake run``` to your heroku scheduler and set to whatever schedule you want.


## Usage

If you have your repo in an env var as above, run the rake task `run`

```
rake run
```

If not, then pass the repo to `run` like

```
rake run repo=owner/repo
```

## Rake tasks

* rake envs  # list env vars
* rake run   # checks for new packages or new releases
