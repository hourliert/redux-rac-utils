# redux-rac-utils
[![Build Status](https://travis-ci.org/FoodMeUp/redux-rac-utils.svg?branch=master)](https://travis-ci.org/FoodMeUp/redux-rac-utils)
[![codecov](https://codecov.io/gh/FoodMeUp/redux-rac-utils/branch/master/graph/badge.svg)](https://codecov.io/gh/FoodMeUp/redux-rac-utils)

This is a set of utils for creating redux actions creators and reducers.

## Getting started
```
npm install --save redux-rac-utils
```

## Creating a reducer
This helper creates a redux reducer. It relies on the fact that an action object must be FSA compliant.

```js
import { reducerFactory } from 'redux-rac-utils';

const initialState = {
  value: 0,
};

const reducer = reducerFactory(
  initialState,
  {
    INC: (state, action) => state + action.payload,
    DEC: (state, action) => state - action.payload,
  }
);

reducer();

/*
{
  value: 0
}
*/

```

## Creating an actions creator

```js
import { actionsCreatorFactory } from 'redux-rac-utils';

const actionsCreator = actionsCreatorFactory(
  'INC'
);

actionsCreator();

/*
{
  type: 'INC'
}
*/

actionsCreator(5);

/*
{
  type: 'INC',
  payload: 5
}
*/

```

You could also provide `payloadCreator` and `metaCreator` (similar to [redux-actions](https://github.com/acdlite/redux-actions)).

```js
import { actionsCreatorFactory } from 'retax';

const actionsCreator = actionsCreatorFactory(
  'INC',
  x => 2 * x,
  y => 3 * y
);

actionsCreator();

/*
{
  type: 'INC'
}
*/

actionsCreator(5);

/*
{
  type: 'INC',
  payload: 10,
  meta: 15
}
*/

```
