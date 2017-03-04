<template lang="markdown">

# 信息窗体

`BmInfoWindow` 信息窗体使用 slot 模式渲染子节点。如果您的浏览器支持 `MutationObserver` 方法，在您更新子节点的时候会自动调整信息窗体的尺寸。如果不支持该方法，您需要在更新子节点后手动调用当前 `BmInfoWindow` 实例的 `overlay.redraw()` 方法更新视图。

## 属性

|属性名|类型|默认值|描述|
|------|:---:|:---:|----|
|show|Boolean|false|信息窗体是否开启|
|position|Point||信息窗体所指坐标|
|width|Number||信息窗宽度，单位像素。取值范围：0, 220 - 730。如果您指定宽度为0，则信息窗口的宽度将按照其内容自动调整|
|height|Number||信息窗高度，单位像素。取值范围：0, 60 - 650。如果您指定高度为0，则信息窗口的高度将按照其内容自动调整|
|maxWidth|Number||信息窗最大化时的宽度，单位像素。取值范围：220 - 730|
|offset|Size||信息窗位置偏移值。默认情况下在地图上打开的信息窗底端的尖角将指向其地理坐标，在标注上打开的信息窗底端尖角的位置取决于标注所用图标的infoWindowOffset属性值，您可以为信息窗添加偏移量来改变默认位置|
|title|String||信息窗标题文字，支持HTML内容|
|autoPan|Boolean|true|是否开启信息窗口打开时地图自动移动|
|closeOnClick|Boolean|true|是否开启点击地图关闭信息窗口|
|message|String|自定义部分的短信内容，可选项。完整的短信内容包括：自定义部分+位置链接，不设置时，显示默认短信内容。短信内容最长为140个字|
|maximize|Boolean|false|允许最大化|

## 事件

|事件名|参数|描述|
|------|:--:|----|
|click|event{type, target, point, pixel}|点击折线后会触发此事件|
|dblclick|event{type, target, point, pixel}|双击折线后会触发此事件|
|mousedown|event{type, target, point, pixel}|鼠标在折线上按下触发此事件|
|mouseup|event{type, target, point, pixel}|鼠标在折线释放触发此事件|
|mouseout|event{type, target, point, pixel}|鼠标离开折线时触发此事件|
|mouseover|event{type, target, point, pixel}|当鼠标进入折线区域时会触发此事件|
|remove|event{type, target}|移除折线时触发|
|lineupdate|event{type, target}|覆盖物的属性发生变化时触发|

## 示例

### 在地图中添加一个信息窗体

#### 代码

```html
<template>
  <baidu-map class="map" :center="{lng: 116.404, lat: 39.915}" :zoom="15">
    <bm-info-window :position="{lng: 116.404, lat: 39.915}" title="Info Window Title" :show="infoWindow.show" @close="infoWindowClose" @open="infoWindowOpen">
      <p v-text="infoWindow.contents"></p>
      <button @click="clear">Clear</button>
    </bm-info-window>
  </baidu-map>
</template>

<script>
export default {
  data () {
    return {
      infoWindow: {
        show: true,
        contents: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
      }
    }
  },
  methods: {
    infoWindowClose (e) {
      this.infoWindow.show = false
    },
    infoWindowOpen (e) {
      this.infoWindow.show = true
    },
    clear () {
      this.infoWindow.contents = ''
    }
  }
}
</script>
```

#### 预览
<doc-preview>
  <baidu-map slot="map" class="map" :center="{lng: 116.404, lat: 39.915}" :zoom="15">
    <bm-info-window :position="{lng: 116.404, lat: 39.915}" title="Info Window Title" :show="infoWindow.show" @close="infoWindowClose" @open="infoWindowOpen">
      <p v-text="infoWindow.contents"></p>
      <button @click="clear">Clear</button>
    </bm-info-window>
  </baidu-map>
  <div slot="bottom" class="mdl-card__actions mdl-card--border">
    <div class="mdl-grid">
      <div class="mdl-cell mdl-cell--6-col mdl-cell--3-offset">
        <label class="mdl-switch mdl-js-switch mdl-js-ripple-effect">
          <input type="checkbox" class="mdl-switch__input" v-model="infoWindow.show" @click="infoWindow.show = !infoWindow.show">
          <span class="mdl-switch__label">信息窗体开关</span>
        </label>
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <textarea class="mdl-textfield__input" type="text" rows= "2" v-model="infoWindow.contents"></textarea>
          <label class="mdl-textfield__label" >信息窗体内容</label>
        </div>
      </div>
    </div>
  </div>
</doc-preview>

</template>

<script>
export default {
  data () {
    return {
      infoWindow: {
        show: true,
        contents: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
      }
    }
  },
  methods: {
    infoWindowClose (e) {
      this.infoWindow.show = false
    },
    infoWindowOpen (e) {
      this.infoWindow.show = true
    },
    clear () {
      this.infoWindow.contents = ''
    }
  }
}
</script>