# Overview

This repo describes how to create `eslint-config`, `prettier-config` and `stylelint-config` with lerna and push them to npm, in order to make the same configurations across different projects.

That benefits because you don't have to update 10 different projects to apply the same rule. Instead, you can update a central repository to push the changes to npm, and pull the changes in these different projects.

# Push your initial shareable configurations to npm

You can fork this repo as a starting point. All you need to do is updating the all `package.json` to change the package name to `@your-name/xxxxx-config` from `@mikamikuh/xxxxx-config`.

Then, push your sharable config to your npm repository

```
$ npm login
$ lerna publish --no-git-tag-version --no-push
```

# In your actual projects

First of all, run `npm install` that you pushed into npm. For example,

```
$ npm install @mikamikuh/eslint-config-vue @mikamikuh/prettier-config @mikamikuh/stylelint-config --save-dev
```

## eslint-config

Create `.eslintrc.js` in your project and

```
module.exports = {
  extends: ['@mikamikuh/eslint-config-vue'],
}
```

## prettier-config

Create `.prettierrc.js` and

```
module.exports = require('@mikamikuh/prettier-config')
```

## stylelint-config

Create `.stylelintrc` and

```
{
    "extends": "@mikamikuh/stylelint-config"
}
```