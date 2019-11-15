# Vue.js

## Design Patterns

### common

일반적인 디자인 방법
상위 요소에서 하위요소로 데이터를 넘겨주는 props를 사용

AppHeader.vue

```js
<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: {
    title: String,
  }
}
</script>
© 2019 GitHub, Inc.

```

App.vue

```js
<template>
  <div>
    <app-header :title="appTitle"></app-header>
    <app-content :items="items" @renew="renewItems"></app-content>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppContent from './components/AppContent.vue';
export default {
  components: {
    AppHeader,
    AppContent,
  },
  data() {
    return {
      appTitle: 'Common Approach',
      items: [10, 20, 30],
    }
  },
  methods: {
    renewItems() {
      this.items = [40, 50, 60];
    },
  },
}
</script>

```

### controlled

기능을 작은 단위로 나누는 방법

CheckBox.vue

```js
<template>
  <input type="checkbox">
</template>

<script>
export default {

}
</script>

```

App.vue

```js
<template>
  <check-box></check-box>
</template>

<script>
import CheckBox from './components/CheckBox.vue';
export default {
  components: {
    CheckBox
  },
}
</script>

```

### renderless

하위 요소에서 변경한 값을 상위요소에서 표현하는 방식

FetchData.vue

```js
<script>
import axios from 'axios';
export default {
  props: ['url'],
  data() {
    return {
      response: null,
      loading: true,
    }
  },
  created() {
    axios.get(this.url)
      .then(response => {
        this.response = response.data;
        this.loading = false;
      })
      .catch(error => {
        alert('[ERROR] fetching the data', error);
        console.log(error);
      });
  },
  render() {
    return this.$scopedSlots.default({
      response: this.response,
      loading: this.loading,
    });
  },
}
</script>

```

App.vue

```js
<template>
  <div>
    <fetch-data url="https://jsonplaceholder.typicode.com/users/1">
      <!-- ... -->
    </fetch-data>
  </div>
</template>

<script>
import FetchData from './components/FetchData.vue'
export default {
  components: {
    FetchData
  },
}
</script>

```

### Slots

하위요소를 템플릿 개념으로 활용하는 방법

특정 부분만 button이나 img 태그를 붙이거나, style을 변경할 수 있어서 for문과 차별화 됨

Item.vue

```js
<template>
  <li>
    <slot>
      <!-- NOTE: 등록하는 곳에서 정의할 화면 영역 -->
    </slot>
  </li>
</template>

```

App.vue

```js
<template>
  <div>
    <ul>
      <item>아이템 1</item>
      <item>아이템 2</item>
      <item>아이템 3</item>
      <item>아이템 4</item>
      <item>아이템 5</item>
    </ul>
  </div>
</template>

<script>
import Item from './Item.vue';
export default {
  components: {
    Item,
  },
}
</script>

```

## Plugins

반복해서 사용하는 외부 라이브러리를 반복해서 불러오지 않게 만들어 줌

페이지 마다 import 반복하는 것을 없앨 수 있음

ex) Chart.js 라이브러리

### main.js

```
Vue.use(ChartPlugin);
```

### plugins/[plugin-name].js

```js
import Chart from "chart.js";

export default {
  install(Vue) {
    Vue.prototype.$_Chart = Chart;
  }
};
```

### use

```js
this.$_Chart;
```

## refs

element를 선택할 때 사용

컴포넌트 내의 선택자라서 충돌을 방지할 수 있음

```html
<div ref="stuff"></div>
```

### use

```js
this.$refs.stuff;
```
