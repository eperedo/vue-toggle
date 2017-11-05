# v-toggle

> a simple a simple toggle component for Vue 2.x.x

> design from [here](https://sketchrepo.com/free-sketch/onoff-switches-freebie/)

### Usage

1. Install from npm

```bash
npm install v-toggle
```

If you are using plain html you can use the umd version from here

```html
<script src="https://unpkg.com/v-toggle/dist/v-toggle.umd.min.js"></script>
```

2. Include as a component in your app

```js

import v-toggle from 'v-toggle';

export default {
  name: 'my-component',
  data() {
    return {
      toggleValue: true,
    };
  },
  components: {
    vToggle, // window.vToggle.default for umd version
  },
};
```

3. Include the component in your template, do not forget the id and v-model property!

```html
<v-toggle id="v-t-default" v-model="toggleValue" />
```

4. That's it! Now you have a simple toggle in your app! 😏

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run component
```
