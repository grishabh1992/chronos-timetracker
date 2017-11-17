[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

## GitFlow
We use [Vincent Driessen's branching model.](http://nvie.com/posts/a-successful-git-branching-model/)  
Read details here:  
- http://nvie.com/posts/a-successful-git-branching-model/  
- https://www.atlassian.com/git/tutorials/comparing-workflows#gitflow-workflow  
- http://danielkummer.github.io/git-flow-cheatsheet/  

Use [git-flow](https://github.com/petervanderdoes/gitflow-avh) package for working with branches.

#### git flow init
Use all init settings as default, except tag prefix, it must be 'v'.


## Commit changes

#### Conventional Commits
We use [conventional commits specification](https://conventionalcommits.org/) for commit messages.

#### Commitzen
To ensure that all commit messages are formatted correctly, we use [Commitizen](http://commitizen.github.io/cz-cli/) in this repository.
It provides interactive interface that creates your commit messages for you.
Running commitizen is as simple as running yarn run commit from the root of the repo.
You can pass all the same flags you would normally use with git commit.

```
  yarn run commit -- -a
```

## Packaging
To package an app for production, please ensure that `MIXPANEL_API_TOKEN` and `SENTRY_API_KEY`
env variables are set.

```
  export MIXPANEL_API_TOKEN=<your_mixpanel_api_token>
  export SENTRY_API_KEY=<your_sentry_api_key>
```

If you don't want to use sentry of mixpanel, you can toggle them with enc variables `DISABLE_MIXPANEL=1` or `DISABLE_SENTRY=1`

```
  export DISABLE_MIXPANEL=1
  export DISABLE_SENTRY=1
```

Then you can package an app with:

#### will include uploading sentry artifacts
```
  yarn package
```

#### will **exclude* uploading sentry artifacts
```
  cross-env UPLOAD_SENTRY=0 yarn package
```


#### will include uploading release to a github
```
  yarn package-release
```


#### will include chrome development tools on production for debugging purposes
```
  yarn package-dev
```

## State architecture
This architecure based on [redux documentation](http://redux.js.org/), so for deeply understanding just read it.

#### To keep clean project's architecture, use these principles:
* [Data normalizing](http://redux.js.org/docs/recipes/reducers/NormalizingStateShape.html) is the most important thing that you have to use.
* [Simple reducer](http://redux.js.org/docs/recipes/reducers/UpdatingNormalizedData.html) I suggest to use "Slice Reducer Composition".
* [Memorized selectors](https://github.com/reactjs/reselect)


## Naming convention
Use airbnb naming conventions:  
- https://github.com/airbnb/javascript/tree/master/react#naming  
- https://github.com/airbnb/javascript#naming-conventions
#### Variables
Use declarative style and avoid single letter names.
If you use abbreveature leave comment with deciphering abbreviations.
#### Selectors
All selectors should have a 'get' prefix.
#### Actions
Actions must begin with some verb - set, fetch, fill, add, delete, etc...


## Containers and Components
* [Simple article about it](https://medium.com/@learnreact/container-components-c0e67432e005)
* [Dan Abramov about it](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)
