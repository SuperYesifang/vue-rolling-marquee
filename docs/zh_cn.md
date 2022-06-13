# vue-rolling-marquee

![vue-rolling-marquee](https://img.shields.io/badge/vue--rolling--marquee-v2.1.3-%23C50008?logo=npm)
![vuejs](https://img.shields.io/badge/vuejs-v2.x-%234FC08D?logo=vuedotjs)
![nodejs](https://img.shields.io/badge/nodejs-lts--v14.x-%23036200?logo=nodedotjs)
[![blog](https://img.shields.io/badge/blog-yesifang.com-orange?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABjFBMVEUAAAAIAQUiBhQVBA05CyK0I2z4MJTgKoV8GEoKAgZyFkT8MZfTKX4dBRFWEDP9MZfMJ3kGAQQHAQTlK4htFUEAHRMATDAAbUQAf1EAh1QAgFAAbUUATDAAHhNMDy7KJngAeUsAKBp9GEr4MJMDAQIAmWEAWzkABAOGGlD9MZYAcUgABQNoFD7mLIoAZUCdHl4ANiKiH2EpCBgAh1UAAgERAwrVKH9nFD0ALBwSAwuqIWXmK4pTEDIAWTgrCBp2F0eVHVmKG1NWETMAdEgAgVAAAQIAJTcATXIAZJQAbqUAap0AVoEAfE4AAQEAN1EAgMAAaEIACQ4Aap4ARiwACQ0AebMAmV8AEwwAAAAAZ5oAZT8AMkkAkFoAEQsAebMAl14AGCQAkl0ALx4AOlYAeEsAGRAATHAAbkUAll0All4AbkYAMB4ATXMABwQAIxYANiIAPicANyIAJBYAQF4AIjIAis0AAgMAhsYAZJYARWYAk9oAHy4ABQcAfbkAO1gAis3/MZgAmmEAld3///8EabibAAAAgHRSTlMACCIVObX54XwKcv3UHVb+zQYH5m0xfrTU4NW1fzJMy8hDffkD/pcHh/69CGjnqJ5ZoynfBBHWZ0kSqudTlCt2lotWwNUCQIOrvrWVzwFe3a4QtnQPz/0gAbKnVe4c0Psp9E9jximBtvj4t0+FCzpaZlo7bTruA+Wtdfs1CNdm7ZpKyEIAAAABYktHRIP8tM/SAAAAB3RJTUUH5QoVBh0NInrzjgAAATtJREFUOMt902VbwzAUBeDLcAYMhru7uzPcXYcP1+EyPMkvZ03TNk0TztfzNnL7BECeCFck/JOo6BiEYuPiVX2CG9EkJsn7ZA9iSUmV9d40ZCYdICMzKzsnNy+/wASFVo+KALCR4hIGSjlQVm4BXFFZRUE1B2q8HMC4tk4D9RxoABvAjRpwuS3QJADcrIkW6witImhrD4OOTtZ7ukAEuFtboqeXjqqvH5xgQL/qoG9oeET/FQIYdQxWAGNmMT4xOTU9MyuCOVbPLywSGhEs6f3yCiFysEr7tXWiABubWu/fIiqwTRfYISqwu0fBvgoc0DlCgCjA4ZF+hWMFODllMzizgfML2l5eXfuNGd7YAARv7+4fHoPc9J/swJlnrn+Rgdc3C4SkT+vd7D8+peDr2+h/FK838Ev3D4W//wNiKCWwWalJAwAAACV0RVh0ZGF0ZTpjcmVhdGUAMjAyMS0xMC0yMVQwNjoyOToxMyswMDowMP1Zb/cAAAAldEVYdGRhdGU6bW9kaWZ5ADIwMjEtMTAtMjFUMDY6Mjk6MTMrMDA6MDCMBNdLAAAAAElFTkSuQmCC)](//yesifang.com)

> 这是一个 Vue 组件，提供一个自动滚动的字幕(跑马灯)。
>
> This is a Vue component that provides an auto-scrolling marquee.

<div align="center">
  <a href="https://nodei.co/npm/vue-rolling-marquee/"><img src="https://nodei.co/npm/vue-rolling-marquee.png?downloads=true&downloadRank=true&stars=true"></a>
</div>

[English Document](../README.md.md)

## 运行简单示例

<img style="display:block;margin: 0 auto" src="./src/assets/img/demo.gif" />

```shell
$ git clone https://github.com/SuperYesifang/vue-rolling-marquee.git
$ cd vue-rolling-marquee
$ npm install
$ npm run dev
```

## 使用

### 1. 在Vue-Cli项目中全局使用

-   main.js

```js
import Vue from "vue";
import VueRollingMarquee from "vue-rolling-marquee";

Vue.use(VueRollingMarquee);

new Vue({
  el: "#app",
  render: h => h(App)
});
```

-   App.vue

```vue
<template>
  <div id="app">
    <vue-rolling-marquee class="vue-rolling-marquee">一些需要滚动显示的内容 ...</vue-rolling-marquee>
  </div>
</template>

<style>
  /* 必须为 vue-rolling-marquee 设置高度 */
  .vue-rolling-marquee {
    height: 400px;
  }
</style>
略...
```

### 2. 在Vue-Cli项目中直接使用

-   App.vue

```vue
<template>
  <div id="app">
    <rolling-marquee>一些需要滚动显示的内容 ...</rolling-marquee>
  </div>
</template>

<script>
  import RollingMarquee from "vue-rolling-marquee";

  export default {
    name: "App",
      components: {
      RollingMarquee
    }
    略...
  };
</script>

<style>
  /* 必须为 vue-rolling-marquee 设置高度 */
  .vue-rolling-marquee {
    height: 400px;
  }
</style>
```

## 选项

vue-rolling-marquee组件接受以下 Vue prop 配置项.

| prop      | 含义                                                                                                | 类型    | 默认值  |
| --------- | ---------------------------------------------------------------------------------------------------------- | ------- | -------- |
| direction | 滚动方向。(接受值: `"top”`,`”right”`,`”bottom”`,`”left”` 或 CSS3 rotateZ 角度值,例如 `30deg`) | String  | `"left"` |
| speed     | 滚动速度。 (单位: `像素/秒`, 备注: 必须是一个正数)                                     | Number  | `30`     |
| duration  | 一次完整滚动所持续的时间。                                                                                | Number  |          |
| shadow    | 开启阴影穿梭效果。 																			 | Boolean | `true`   |
| prompt    | 开启提词器模式。                                    											 | Boolean | `false`  |
| promptGap | 内容块的穿梭部分和未梭部分间的间隙宽度. (单位: `像素`) | Number  | `20`     |
| rid | 跑马灯的唯一ID，用于防止多个跑马灯之间的冲突，通常由组件自动生成，无需人为设置 | Number、String| |

## 详细解释选项

以下对各配置想进行详细解释

### direction

该配置项用于配置内容的滚动的方向.

-   支持这些预设的关键字: `"left"`，`"right"`, `"bottom"`, `"left"`.
-   支持CSS3的类似rotateZ的角度调节方式, 例如: `"45deg"`, `"-128deg"`.

> 预设关键字含义表:

| 关键字    | 含义       | 等价角度值 |
| ---------- | ----------------- | ---------------- |
| `"top"`    | 向上滚动    | `"0deg"`         |
| `"right"`  | 向右滚动  | `"90deg"`        |
| `"bottom"` | 向下滚动 | `"180deg"`       |
| `"left"`   | 向左滚动   | `"270deg"`       |

### speed & duration

这两个选项都是用于控制滚动速度的。 **speed** 优先于 **duration**.

-   speed: 设置滚动的速度。 (单位：`像素/秒`, 默认值: `30`)
-   duration: 设置一次完整滚动所消耗的时间. (单位: `毫秒`)

### shadow

开启阴影穿梭效果。 当内容块部分离开可见区域时，将会出现一个影子从另一侧进入可见区域。

### prompt

开启提词器模式。当可视区域可以容纳内容时，内容将显示为普通内容，当可视区域无法容纳内容时，将会进行滚动显示，类似于提词器。

### promptGap

当开启阴影穿梭时。内容块与影子之间间隙的宽度。 (单位: `像素`)