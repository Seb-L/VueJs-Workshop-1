# Vue-beer

Build your first VueJs App!

## VueJs

[VueJs Basic Example](https://jsfiddle.net/etb0gymv/27/)

## Result

![result](./result.png)

The final result is composed of a paginated list of beers fetched with an HTTP request with a filter input, and a selected beer details area.

## Install project sources

### 1. With Npm and node

If you already have node and npm installed, open a terminal in one of the "step" folder then type:

```bash
npm install && npm run dev
```

or with yarn

```bash
yarn install && yarn run dev
```

### 2. With Docker

If you don't have node and npm or you don't want to update your local node version, use docker

## Step 1: HTTP Request and list rendering

**Specs:**

- HTTP Request to https://api.punkapi.com/v2/beers (GET) in the home component
- Create a BeerList component that render a list of beers with the data from "home" component

**Hints:**

- v-for: https://vuejs.org/v2/guide/list.html#v-for
- vue-axios: https://www.npmjs.com/package/vue-axios (already installed)
- "mounted" hook
- Dynamic props: https://vuejs.org/v2/guide/components.html#Props

## Step 2: Details panel and passing data between components

**Specs:**

- Create a BeerDetails component with the selected beer infos
- Add a "selected" state on the selected beer in "BeerList" component

**Hints:**

- Custom event "$emit input" and v-model: https://vuejs.org/v2/guide/components.html#Form-Input-Components-using-Custom-Events
- Class Binding / Object Syntax: https://vuejs.org/v2/guide/class-and-style.html#Object-Syntax
- Dynamic props: https://vuejs.org/v2/guide/components.html#Props

## Step 3: Filter by name and beer list paginate

**Specs:**

- add a filter input above the beer list in BeerList component
- add paginate buttons under the beer list in BeerList component

**Hints:**

- Computed properties

## Bonus: Vuex

- Using vuex to store and access the data instead of using dynamic properties

## Resources

- Docs and guides: https://vuejs.org/v2/guide/
- Official examples: https://vuejs.org/v2/examples/index.html
- VueJs CheatSheet: https://vuejs-tips.github.io/cheatsheet/


