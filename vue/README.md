# Vue.js

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
