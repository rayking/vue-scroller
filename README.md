# Vue Scroller ![version](https://img.shields.io/badge/version-%20v2.2.0%20-green.svg) ![vue](https://img.shields.io/badge/vue-%20v2.1%20-green.svg) 

[Vue Scroller](https://github.com/wangdahoo/vue-scroller) is a foundational component of [Vonic](https://github.com/wangdahoo/vonic) UI.
In purpose of smooth scrolling, pull to refresh and infinite loading.

> For vue 1.0, please refer to branch v1.

## Demo

[https://wangdahoo.github.io/vue-scroller/](https://wangdahoo.github.io/vue-scroller/)

## How to use

```bash
npm i vue-scroller -S
```

```js
/* ignore this if you include vue-scroller.js by <script> tag from a cdn, such as unpkg */
import Vue from 'vue'
import VueScroller from 'vue-scroller'
Vue.use(VueScroller)
```

```html
<scroller 
  :on-refresh="refresh"
  :on-infinite="infinite">
  <!-- content goes here -->
</scroller>
```

[Live Code on JsFiddle](https://jsfiddle.net/wangdahoo/cpjfr096/)

## Webpack project by vue-cli

https://github.com/wangdahoo/vue-scroller-demo

## API

#### Scroller component attributes:

| Attr. Name | Description | Required | Default Value |
|-----|-----|-----|-----|
| onRefresh | pull to refresh callback | N | - |
| onInfinite | infinite loading callback | N | - |
| onEndTouch | sroll end callback with offset top value | N | - |
| refreshText | tips of `pull-to-refresh` | N | 下拉刷新 |
| noDataText | tips of `no-more-data` when `infinite-loading` finished | N | 没有更多数据 |
| width | scroller container width | N | `100%` |
| height | scroller container height | N | `100%` |
| snapping | enable snapping mode | N | `false` |
| snappingWidth | snapping width | N | 100 (stand for 100px) |
| snappingHeight | snapping height | N | 100 |
| refreshLayerColor | text color of `pull-to-refresh` layer | N | #AAA |
| loadingLayerColor | text color of `infinite-loading` layer | N | #AAA |
| minContentHeight | min content height (px) of `scroll-content` | N | 0 |

#### Scroller vm instance methods:

- `resize()` resize scroller content (**deprecated, cause the scroller's content resizes self automatically**)
- `triggerPullToRefresh()` start pull-to-refresh manually
- `finishPullToRefresh()` stop pull-to-refresh
- `finishInfinite(isNoMoreData :Boolean)` stop infinite-loading
- `scrollTo(x:Integer, y:Integer, animate:Boolean)` scroll to a position in scroller content
- `scrollBy(x:Integer, y:Integer, animate:Boolean)` scroll by a position in scroller content
- `getPosition :Object` get current position of scroller content

#### 改动点：
- onRefresh： 触发条件改为在执行状态不会再次触发回调方法，防止远程拉去数据时，服务端还未返回又向服务器发起第二次请求
- 新增接口 onEndTouch：用户滚动完毕后触发，回调值为当前距离顶部的像素值